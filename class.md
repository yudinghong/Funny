## 总体架构
```puml
namespace Funny {
  class Application
  class Http
  class ThreadPool
  class RegExp
  class Url
  class JsonParse
  class HtmlParse
  class Log

  Application *-- Http
  Application *-- ThreadPool
  Application *-- RegExp
  Application *-- Url
  Application *-- JsonParse
  Application *-- HtmlParse
  Application *-- Log
}
```
## 各个类关系
```puml
Http *-- TcpServer
Http *-- TcpClient
```

```puml
TcpServer *-- ThreadPool
```

```puml
class RegExp
```

```puml
class Url
```

```puml
class JsonParse
```

```puml
XmlParse <|-- HtmlParse
```

```puml
class Log
```

## 类介绍

### ThreadPool

### TcpEnum

```puml
enum TcpError {
  TCP_NO_ERROR,
  TCP_INIT_WSA_STARTUP_FAILED,
  TCP_INIT_FAILED,
  TCP_INIT_WITHOUT_IP,
  TCP_INIT_WITHOUT_PORT,
  TCP_CONNECT_TO_HOST_FAILED
}
```

### TcpClinent
```puml
class TcpClient {
  + TcpClient(string ip, int port, bool async)
  + ~TcpClient()
  + bool start()
  + bool startWithResponse(char *response, int respLength)
  + bool startWithResponse(string response)
  + string getIP()
  + int getPort()
  + bool isAsync()
  + void setIP(string ip)
  + void setPort(int port)
  + void setAysnc(bool async)
  + bool isConnected()
  + TCP_ERROR getLastError()
  + int send(string message)
  + int send(char *message, int len)
  + function<void<char *, int, SOCKET>> asyncCallback
  - string m_ip
  - int m_port
  - bool m_async
  - SOCKET socketObject
  - void initClient()
  - void setLastError(TCP_ERROR error)

}
```

### TcpServer

