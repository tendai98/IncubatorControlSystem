### Documentation: Working Progress


### Function Descriptions

#### File: IncubatorControlSystem.ino

- `setup()`: Initializes the system components, including Wi-Fi, web server, MCP, DHT11 sensor, and relays.

- `loop()`: The primary control loop of the system. It collects sensor data, manages temperature and rotation, handles web server requests, and ensures continuous system operation.

#### File: mcp.h

##### EEPROM Parameter Handling

- `saveParameters(float temp1, float temp2, int rotationTimer, float tempOffset, int rotorSleepTimer)`: Saves critical system parameters like temperature thresholds and rotation timings to EEPROM memory for persistent storage.

- `loadParameters()`: Retrieves stored parameters from EEPROM memory during system initialization, ensuring previous settings are applied.

- `initMCP()`: Initializes the EEPROM memory and loads system parameters during system startup.

##### Rotation Control

- `getState(int state)`: Determines the current rotation state (forward or reverse) and updates the rotation counter accordingly.

- `computeState()`: Manages the rotation state and direction based on a timer, ensuring even egg rotation for uniform development.

- `controlRelay()`: Controls the relay responsible for egg rotation, managing its state based on rotation timing and direction.

- `rotateRelayControl()`: Integrates state management and relay control to facilitate smooth egg rotation.

##### Temperature Control

- `runMCP()`: Monitors temperature thresholds and controls the relay for temperature regulation. It ensures the temperature remains within the predefined range.

#### File: relays.h

- `initRelays()`: Initializes the relay modules, configuring their pins as outputs and setting their initial states.

- `setRelayState(int index, int state)`: Controls the specified relay (temperature or rotation) by setting its state (ON/OFF) based on the given index and state values.

#### File: wifi.h

- `initWiFi()`: Configures the ESP8266 Microcontroller to create a Wi-Fi access point, allowing users to connect and interact with the incubator system through the web interface.

#### File: server.h

##### Web Server Functions

- `rotationRelayControlOverride()`: Allows users to manually control the rotation mechanism through the web interface, enabling or disabling rotation as needed.

- `tempRelayControlOverride()`: Enables manual control of the temperature regulation, allowing users to turn the heating element on or off based on their requirements.

- `enableControlOverride()`: Enables or disables the manual control override feature, allowing users to manually manage temperature and rotation settings temporarily.

- `getStatusData()`: Gathers and sends system status data, including temperature, humidity, relay states, and control settings, to the connected clients via the web server.

- `setParameters()`: Allows users to set custom system parameters, such as temperature thresholds and rotation timings, through the web interface, ensuring flexibility in operation.

- `resetICS()`: Provides a function to reset the entire incubator system, allowing users to start fresh if necessary.

- `getId()`: Sends the unique identifier (SSID) of the incubator system's Wi-Fi access point to connected clients.

- `deadend()`: Handles any undefined or incorrect web server requests, returning an error response to the client.

- `initServer()`: Initializes the web server, setting up various routes and handlers for incoming client requests. It prepares the server to manage user interactions effective
