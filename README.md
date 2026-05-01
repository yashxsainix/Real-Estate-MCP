# Real Estate MCP Server

A comprehensive Model Context Protocol (MCP) server for real estate data management. This server provides tools, resources, and prompts for property listings, agent management, market analysis, client relationships, and area intelligence.

## 🏗️ Architecture

The server is built with a modular, componentized architecture for maintainability and scalability:

```
real-estate-mcp/
├── main.py                    # Main server entry point
├── utils.py                   # Core data management utilities
├── tools/                     # MCP Tools (organized by category)
│   ├── property_tools.py      # Property search, filtering, insights
│   ├── agent_tools.py         # Agent profiles, performance, dashboards
│   ├── market_tools.py        # Market analysis and trends
│   ├── client_tools.py        # Client management and matching
│   ├── area_tools.py          # Area intelligence and amenities
│   └── system_tools.py        # Data management and system tools
├── resources/                 # MCP Resources (organized by domain)
│   ├── property_resources.py  # Property-related resources
│   ├── agent_resources.py     # Agent-related resources
│   ├── market_resources.py    # Market analysis resources
│   ├── client_resources.py    # Client management resources
│   └── location_resources.py  # Area and amenity resources
├── prompts/                   # MCP Prompts (user-controlled templates)
│   ├── __init__.py            # Central prompt registration
│   ├── property_prompts.py    # Property analysis and comparison prompts
│   ├── client_prompts.py      # Client matching and consultation prompts
│   ├── market_prompts.py      # Market analysis and investment prompts
│   └── agent_prompts.py       # Agent performance and development prompts
└── data/                      # Real estate data files
    ├── properties/
    ├── agents/
    ├── clients/
    ├── market/
    ├── transactions/
    ├── areas/
    └── amenities/
```

## 🚀 Features

### MCP Capabilities
- **30+ Tools**: Comprehensive real estate operations
- **10 Resources**: 5 static resources + 5 dynamic resource templates
- **11 Prompts**: User-controlled analysis templates across 4 categories
- **SSE Transport**: Web-compatible Server-Sent Events endpoint

### Tool Categories

#### 🏠 Property Management (7 tools)
- Search and filter properties by multiple criteria
- Get property details and comprehensive insights
- Area-based and agent-based property listings
- Market context and comparable analysis

#### 👥 Agent Operations (6 tools)
- Agent profiles and specializations
- Performance dashboards and metrics
- Client and property portfolio management
- Sales tracking and analytics

#### 📊 Market Analysis (7 tools)
- Market overview and price analytics
- Area-specific market performance
- Investment opportunity analysis
- Comparative area analysis
- Transaction tracking

#### 🤝 Client Management (3 tools)
- Client profiles and preferences
- Property matching algorithms
- Budget and criteria-based recommendations

#### 🏘️ Area Intelligence (9 tools)
- Comprehensive area reports
- Amenities and demographics
- Schools, parks, shopping, healthcare data
- City overview and area comparisons

#### ⚙️ System Management (2 tools)
- Data refresh and cache management
- System statistics and summaries

### Resources

#### Static Resources
- `realestate://all-properties`: Complete property listings
- `realestate://all-agents`: Agent directory
- `realestate://market-overview`: Current market trends
- `realestate://all-areas`: Area information
- `realestate://amenities`: Complete amenities database

#### Dynamic Resource Templates
- `realestate://properties/area/{area}`: Area-specific properties
- `realestate://agent/{agent_id}/dashboard`: Agent performance dashboard
- `realestate://market/area/{area}`: Area market analysis
- `realestate://property/{property_id}/insights`: Property insights
- `realestate://client/{client_id}/matches`: Client property matches

### Prompts (11 total)

#### Property Prompts (2 prompts)
- **Property Analysis**: Comprehensive property evaluation and insights
- **Property Comparison**: Side-by-side property comparison analysis

#### Client Prompts (3 prompts) 
- **Client Matching**: Personalized property recommendations
- **Client Consultation**: Structured consultation framework
- **Client Feedback Analysis**: Search strategy refinement

#### Market Prompts (3 prompts)
- **Market Reports**: Comprehensive area market analysis
- **Investment Analysis**: ROI and opportunity assessment
- **Comparative Market Analysis**: Multi-area comparison

#### Agent Prompts (3 prompts)
- **Agent Performance**: Performance dashboards and analysis
- **Agent Marketing Strategy**: Business development and marketing
- **Agent Training Development**: Skill enhancement and training plans

## 📦 Installation

### Quick Start (Recommended)

```bash
# Clone the repository
git clone https://github.com/agentic-ops/real-estate-mcp.git
cd real-estate-mcp

# Create and activate virtual environment
python -m venv .venv

# On Windows:
.venv\Scripts\activate

# On macOS/Linux:
source .venv/bin/activate

# Install dependencies
pip install -r requirements.txt

# Install in Claude Desktop
mcp install main.py
```

### Manual Claude Desktop Configuration

If you prefer manual setup, edit your Claude Desktop config file:

**Windows**: `%APPDATA%\Claude\claude_desktop_config.json`  
**macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "real-estate": {
      "command": "C:/absolute/path/to/real-estate-mcp/.venv/Scripts/python.exe",
      "args": ["C:/absolute/path/to/real-estate-mcp/main.py"],
      "env": {
        "PYTHONUNBUFFERED": "1"
      }
    }
  }
}
```

**Important**: 
- Use **absolute paths** for both the Python executable and main.py
- On Windows, use forward slashes (/) or double backslashes (\\\\) in the JSON
- Point to your **virtual environment's Python** (`.venv/Scripts/python.exe` on Windows, `.venv/bin/python` on macOS/Linux)
- Restart Claude Desktop completely after configuration

### Running Locally (For Testing)

```bash
# STDIO mode (default, for Claude Desktop)
python main.py

# SSE mode (for remote/web access)
python main.py sse
```

## 🔍 MCP Inspector

To inspect and debug your MCP server during development:

```bash
npx @modelcontextprotocol/inspector python main.py
```

This will launch the MCP Inspector interface, allowing you to:
- Monitor MCP messages in real-time
- Debug tool and resource calls
- Inspect server responses
- Test server functionality

## 💻 Claude Desktop Integration

### Quick Setup

Once your server is installed in Claude Desktop (see Installation above), you can immediately start using it:

1. **Restart Claude Desktop** after configuring the server
2. **Look for the MCP indicator** (🔨 hammer icon) in the bottom-right corner
3. **Click the indicator** to see available tools and resources
4. **Start chatting** - Claude can now access all your real estate data!

### Example Prompts for Claude

Try these prompts to explore the real estate data:

- *"What properties are available in Downtown Riverside?"*
- *"Show me properties between $500k and $1M"*
- *"Give me agent Sarah Chen's performance dashboard"*
- *"What's the current market overview?"*
- *"Match properties for client CLI001"*
- *"Tell me about schools in the Woodcrest area"*
- *"Compare market conditions across all areas"*

### Configuration Details

**Windows**: Edit `%APPDATA%\Claude\claude_desktop_config.json`
**macOS**: Edit `~/Library/Application Support/Claude/claude_desktop_config.json`

```json
{
  "mcpServers": {
    "real-estate": {
      "command": "python",
      "args": ["C:/absolute/path/to/real-estate-mcp/main.py"],
      "env": {
        "PYTHONUNBUFFERED": "1"
      }
    }
  }
}
```

**Important Notes:**
- Use **absolute paths** to your `main.py` file
- Adjust the Python command if you're using a virtual environment
- The server runs in STDIO mode by default (no port or URL needed)

## 🌐 Server Transport Modes

This server supports two transport modes for different use cases:

### STDIO Transport (Default - Recommended for Claude Desktop)

**Best for**: Claude Desktop, MCP Inspector, local development

**Advantages**:
- ✅ Ultra-low latency (~1ms)
- ✅ Simple configuration (no ports/URLs)
- ✅ Automatic process management
- ✅ Standard MCP ecosystem compatibility

**Usage**:
```bash
python main.py
```

### SSE Transport (For Remote/Web Access)

**Best for**: Remote access, web integration, team sharing, cloud deployment

**Advantages**:
- ✅ Multiple simultaneous clients
- ✅ Remote access over network
- ✅ Web browser compatible
- ✅ Real-time streaming updates

**Usage**:
```bash
python main.py sse
```

### SSE Connection Details (When Running in SSE Mode)
- **SSE Endpoint**: `http://127.0.0.1:8000/sse` (for establishing SSE connection)
- **Message Endpoint**: `http://127.0.0.1:8000/messages/` (for posting MCP messages)
- **Transport**: SSE (Server-Sent Events)
- **Protocol**: MCP (Model Context Protocol)

### Web Client Example
```javascript
// Establish SSE connection
const eventSource = new EventSource('http://127.0.0.1:8000/sse');
eventSource.onmessage = function(event) {
    const mcpMessage = JSON.parse(event.data);
    // Handle MCP protocol messages
};

// Send MCP messages
async function sendMCPMessage(message) {
    const response = await fetch('http://127.0.0.1:8000/messages/', {
        method: 'POST',
        headers: {
            'Content-Type': 'application/json',
        },
        body: JSON.stringify(message)
    });
    return response.json();
}
```

## 🔧 Component Details

### Core Components

#### `utils.py` - Data Management
- `RealEstateDataManager`: Central data access class
- `PropertyFilter`: Search and filtering utilities
- JSON data loading and caching
- Cross-referencing and relationship mapping

#### `main.py` - Server Entry Point
- FastMCP server initialization
- Component registration orchestration
- SSE transport configuration
- Startup logging and diagnostics

### Tool Modules

Each tool module follows a consistent pattern:
```python
def register_[category]_tools(mcp: FastMCP):
    """Register all [category] tools with the MCP server"""
    
    @mcp.tool()
    def tool_function(parameters) -> str:
        """Tool description"""
        # Implementation
        return json.dumps(result, indent=2)
```

### Resource Modules

Resources are organized by domain for better maintainability:

#### Property Resources (`property_resources.py`)
- Property listings and search results
- Property insights and market context
- Area-based property filtering

#### Agent Resources (`agent_resources.py`)
- Agent profiles and directories
- Performance dashboards and metrics

#### Market Resources (`market_resources.py`)
- Market overview and trends
- Area-specific market analysis

#### Client Resources (`client_resources.py`)
- Client preference matching
- Property recommendations

#### Location Resources (`location_resources.py`)
- Area information and demographics
- Amenities and local services

Each module follows a consistent pattern:
```python
def register_[domain]_resources(mcp: FastMCP):
    """Register all [domain] resources with the MCP server"""
    
    @mcp.resource("realestate://resource-name")
    def resource_function() -> str:
        """Resource description"""
        return json.dumps(data, indent=2)
```

### Prompt Templates

Prompts guide AI analysis:
```python
@mcp.prompt()
def analysis_prompt(param: str = "default") -> str:
    """Analysis prompt description"""
    return f"""
    Detailed analysis instructions for {param}...
    """
```

## 📊 Data Structure

The server operates on comprehensive real estate data:

- **5 Properties**: Victorian homes, contemporary, luxury, townhouses
- **3 Agents**: Specialized real estate professionals
- **6 Clients**: Buyers, sellers, investors with preferences
- **Multiple Sales**: Recent transaction history
- **5 Areas**: Downtown Riverside, Woodcrest, Canyon Crest, Arlington Heights, La Sierra
- **Amenities**: Schools, parks, shopping, healthcare facilities

## 🔍 Usage Examples

### Using with Claude Desktop (STDIO Mode - Recommended)

After installing in Claude Desktop, simply chat with Claude:

**User**: *"What properties are available in Downtown Riverside?"*

**Claude**: *Uses the `search_properties` tool and reads the `realestate://properties/area/Downtown Riverside` resource to show you all matching properties.*

**User**: *"Show me Sarah Chen's performance dashboard"*

**Claude**: *Reads the `realestate://agent/AG001/dashboard` resource to display comprehensive agent metrics.*

**User**: *"Find properties under $800k with 3+ bedrooms"*

**Claude**: *Uses the `filter_properties` tool with your criteria and presents matching listings.*

### Using with MCP Inspector (For Testing)

```bash
# Test with MCP Inspector
npx @modelcontextprotocol/inspector python main.py
```

Then explore tools and resources through the inspector UI.

### Using with SSE Transport (For Remote/Web Access)

For proper MCP client integration over HTTP, use the MCP protocol with the correct endpoints:

```bash
# Start server in SSE mode
python main.py sse
```

```bash
# Establish SSE connection (listen for server messages)
curl -N http://127.0.0.1:8000/sse

# Send MCP messages (in a separate terminal)
# Search properties
curl -X POST http://127.0.0.1:8000/messages/ \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc": "2.0", "id": 1, "method": "tools/call", "params": {"name": "search_properties", "arguments": {"query": "Victorian"}}}'

# Filter by criteria
curl -X POST http://127.0.0.1:8000/messages/ \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc": "2.0", "id": 2, "method": "tools/call", "params": {"name": "filter_properties", "arguments": {"min_price": 500000, "max_price": 1000000}}}'

# Get market overview
curl -X POST http://127.0.0.1:8000/messages/ \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc": "2.0", "id": 3, "method": "resources/read", "params": {"uri": "realestate://market-overview"}}'

# Match client preferences
curl -X POST http://127.0.0.1:8000/messages/ \
  -H "Content-Type: application/json" \
  -d '{"jsonrpc": "2.0", "id": 4, "method": "tools/call", "params": {"name": "match_client_preferences", "arguments": {"client_id": "CLI001"}}}'
```

### Using SSE Mode with Claude Desktop

If you want to run the server in SSE mode and connect from Claude Desktop (for remote scenarios):

1. Start server: `python main.py sse`
2. Configure Claude Desktop with `mcp-remote`:

```json
{
  "mcpServers": {
    "real-estate-remote": {
      "command": "npx",
      "args": ["-y", "mcp-remote", "http://127.0.0.1:8000/sse"]
    }
  }
}
```

## 🧪 Testing

The project includes a comprehensive test suite covering all components and functionality.

### Test Structure

```
tests/
├── conftest.py              # Pytest configuration and shared fixtures
├── unit/                    # Unit tests for core components
│   ├── test_utils.py        # RealEstateDataManager and PropertyFilter tests
│   └── test_*.py            # Additional unit tests
├── integration/             # Integration tests for MCP components
│   ├── test_property_tools.py    # Property tools integration tests
│   ├── test_all_tools.py         # All other tool categories
│   ├── test_resources.py         # Static and template resources tests
│   └── test_prompts.py            # Prompt template tests
└── __init__.py
```

### Test Categories

#### Unit Tests (`tests/unit/`)
- **Data Manager Tests**: Core functionality of `RealEstateDataManager`
- **Filter Tests**: Property filtering logic and edge cases
- **Utility Functions**: Helper functions and data validation

#### Integration Tests (`tests/integration/`)
- **Property Tools**: Search, filter, insights, and area-based queries
- **Agent Tools**: Profile management, performance dashboards
- **Market Tools**: Market analysis and trend calculations
- **Client Tools**: Client matching and preference algorithms
- **Area Tools**: Area intelligence and amenities data
- **System Tools**: Data refresh and system statistics
- **Resources**: Static resources and dynamic templates
- **Prompts**: Template generation and parameter handling (11 prompts across 4 categories)

### Running Tests

#### Prerequisites
```bash
# Install testing dependencies
pip install -r requirements.txt
```

#### Quick Test Commands
```bash
# Run all tests
pytest

# Run with coverage report
pytest --cov=. --cov-report=html

# Run specific test categories
pytest tests/unit/                    # Unit tests only
pytest tests/integration/             # Integration tests only
pytest tests/integration/test_property_tools.py  # Property tools only
```

#### Using the Test Runner Script
```bash
# Run all tests
python run_tests.py

# Run specific test types
python run_tests.py unit              # Unit tests only
python run_tests.py integration       # Integration tests only
python run_tests.py property          # Property tools only
python run_tests.py resources         # Resource tests only

# Run with verbose output and coverage
python run_tests.py all -v -c
```

### Test Features

#### Fixtures and Test Data
- **Isolated Test Environment**: Each test uses temporary data directories
- **Mock Data**: Consistent test data across all test cases
- **Shared Fixtures**: Reusable test components in `conftest.py`
- **Data Manager Mocking**: Isolated testing without file system dependencies

#### Coverage and Reporting
- **Code Coverage**: Comprehensive coverage reporting with pytest-cov
- **HTML Reports**: Visual coverage reports in `htmlcov/index.html`
- **Missing Lines**: Identification of uncovered code paths
- **Branch Coverage**: Logic branch testing

#### Test Configuration
- **pytest.ini**: Centralized test configuration
- **Automatic Discovery**: Tests auto-discovered by naming convention
- **Parallel Execution**: Support for parallel test execution
- **Filtering**: Warning filters for clean test output

### Test Data Validation

The test suite validates:
- ✅ All 30+ tools function correctly with mock and real data
- ✅ Property filtering logic handles edge cases
- ✅ Search functionality is case-insensitive and comprehensive
- ✅ Agent performance calculations are accurate
- ✅ Market analysis tools process data correctly
- ✅ Client matching algorithms work as expected
- ✅ Area intelligence aggregates data properly
- ✅ Resource endpoints return valid JSON
- ✅ Prompt templates generate proper instructions
- ✅ Error handling for missing or invalid data
- ✅ Data refresh and caching mechanisms
- ✅ System statistics and summaries

### Continuous Integration

For CI/CD pipelines, use:
```bash
# Basic test run
pytest tests/ --tb=short

# With coverage for CI reporting
pytest tests/ --cov=. --cov-report=xml --cov-report=term-missing

# Specific test categories for staged testing
pytest tests/unit/ --tb=short          # Fast unit tests first
pytest tests/integration/ --tb=short   # Integration tests second
```

### Writing New Tests

When adding new functionality:

1. **Unit Tests**: Add to `tests/unit/` for core logic
2. **Integration Tests**: Add to appropriate `tests/integration/test_*.py`
3. **Use Fixtures**: Leverage existing fixtures in `conftest.py`
4. **Mock External Dependencies**: Use `unittest.mock` for isolation
5. **Test Edge Cases**: Include boundary conditions and error scenarios
6. **Follow Naming Convention**: `test_*.py` files, `Test*` classes, `test_*` methods

## 🛠️ Development

### Adding New Tools
1. Choose appropriate category in `tools/`
2. Add tool function with `@mcp.tool()` decorator
3. Register in the category's `register_*_tools()` function
4. Import and call registration in `main.py`
5. **Add Tests**: Create corresponding tests in `tests/integration/`

### Adding New Resources
1. Choose appropriate domain module in `resources/` (property, agent, market, client, location)
2. Add resource function with `@mcp.resource()` decorator and URI pattern
3. Register in the domain's `register_*_resources()` function
4. Import and call registration in `main.py`
5. **Add Tests**: Include resource tests in `tests/integration/test_resources.py`

### Adding New Prompts
1. Choose appropriate category in `prompts/` (property, client, market, or agent)
2. Add prompt function with `@mcp.prompt()` decorator
3. Include parameter defaults and comprehensive instructions
4. Register in the category's `register_*_prompts()` function
5. **Add Tests**: Include prompt tests in `tests/integration/test_prompts.py`

### Adding New Prompt Categories
1. Create new file in `prompts/` directory (e.g., `prompts/new_category_prompts.py`)
2. Follow the existing pattern with `register_new_category_prompts(mcp)` function
3. Import and register in `prompts/__init__.py`
4. **Add Tests**: Create corresponding test fixtures and test methods

## 🎯 Transport Selection Guide

Choose the right transport mode for your use case:

| Feature | STDIO (Default) | SSE (Remote) |
|---------|----------------|--------------|
| **Best For** | Claude Desktop, local tools | Web apps, remote access, team sharing |
| **Latency** | ~1ms (ultra-fast) | 10-100ms (network-dependent) |
| **Multiple Clients** | ❌ Single client | ✅ Multiple simultaneous clients |
| **Remote Access** | ❌ Local only | ✅ Network access |
| **Setup Complexity** | ✅ Simple (no config) | ⚠️ Requires port/URL management |
| **Claude Desktop** | ✅ Native support | ⚠️ Requires mcp-remote proxy |
| **Auto-cleanup** | ✅ Automatic | ⚠️ Manual management |
| **Security** | ✅ Process isolation | ⚠️ Needs authentication |

### Quick Decision Matrix

**Use STDIO when:**
- Installing in Claude Desktop (recommended)
- Running on the same machine as the client
- You want the fastest response times
- You need simple setup with no configuration

**Use SSE when:**
- Deploying to a remote server or cloud
- Multiple team members need access
- Building web applications
- You need real-time streaming updates

## 🚀 Publishing to Repository

### Recommended Approach

The server is **designed to work best with STDIO transport** for the MCP ecosystem, making it:

1. ✅ **Easy to install**: `mcp install main.py`
2. ✅ **Compatible with Claude Desktop**: Standard integration
3. ✅ **Discoverable**: Can be listed in MCP server directories
4. ✅ **Simple to use**: No port configuration needed
5. ✅ **Flexible**: SSE mode available for advanced use cases

### For End Users

**Primary use case** (98% of users):
```bash
git clone https://github.com/agentic-ops/real-estate-mcp.git
cd real-estate-mcp
pip install -r requirements.txt
mcp install main.py --name "Real Estate"
```

**Advanced use case** (remote deployment):
```bash
python main.py sse  # Run on server
# Configure clients to connect to http://your-server:8000/sse
```

## 📝 License

This project is licensed under the MIT License.

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Add your component following the established patterns
4. Test thoroughly
5. Submit a pull request

---

## 📖 Further Reading

For a comprehensive deep dive into the architecture, design principles, and real-world applications of this MCP server, read the detailed blog post:

**[🔌 MCP Servers - Model Context Protocol Implementation](https://edwin.genego.io/ai/mcp-servers)**

The blog post covers:
- Understanding MCP Servers and their business impact
- Architecture deep dive with code examples
- MCP Tools, Prompts, and Resources explained
- Real-world usage scenarios and implementation patterns
- Security considerations and best practices
- Future implications of MCP technology

---

*Built with the Model Context Protocol (MCP) for seamless AI integration* 