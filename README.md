# SToolkit.Network
High performance, powerful, async TCP\UDP socket client\server.
# Install


[Nuget Package](https://www.nuget.org/packages/SToolkit.SocketNetwork/)


Or Nuget console
```
Install-Package SToolkit.SocketNetwork
```
# Usage SocketServer
Including
```C#
using SToolkit.SocketNetwork;
```
Create server, TCP
```C#
SocketServer TcpServer = new SocketServer(NetworkType.Tcp, IPAddress.Loopback, 5400);
```
or UDP
```C#
SocketServer UdpServer = new SocketServer(NetworkType.Udp, IPAddress.Loopback, 5401);
```
Then bind delagates
- **OnConnected** - Called when new client connected
- **OnDisconnected** - Called when client disconnected
- **OnReceived** - Called when received data from client
- **OnError** - Called when server catch error
- **OnStart** - Called when server started
- **OnStop** - Called when server stoppped
Start server
```C#
TcpServer.Start();
UdpServer.Start();
```
All server functions
```C#
SocketServer(NetworkType type, IPAddress address, int port);
void Dispose();
void Start();
void Stop();
```
All server variables
```C#
string Uid;
IPAddress IPAddress;
int Port;
List<ClientConnection> ConnectedClients;
int LoopInterval;
int Backlog;
NetworkType ServerType;
bool UDPClientManage;
int UDPDataInterval;
```
# Usage SocketClient
Icluding
```C#
using SToolkit.SocketNetwork;
```
Create client, TCP
```C#
SocketClient TcpClient = new SocketClient(NetworkType.Tcp);
```
or UDP
```C#
SocketClient UdpClient = new SocketClient(NetworkType.Udp);
```
Bind delegates
- **OnConnected** - Called when client connected
- **OnDisconnected** - Called when client disconnected
- **OnReceived** - Called when received data from server
- **OnError** - Called when client catch error
Connect to remote server
```C#
TcpClient.Connect(IPAddress.Loopback, 5400);
UdpClient.Connect(IPAddress.Loopback, 5401);
```
All client functions
```C#
SocketClient(NetworkType type);
void Dispose();
void Connect(IPAddress address, int port);
void Connect(IPEndPoint point);
void Disconnect();
```
All client variables
```C#
NetworkType ClientType;
int LoopInterval;
int UDPDataInterval;
```
