# 4.Execution_of_NetworkCommands
## AIM :
Use of Network commands in Real Time environment
## Software : 
Command Prompt And Network Protocol Analyzer
## Procedure:
```
To do this EXPERIMENT- follows these steps:

In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
All commands related to Network configuration which includes how to switch to privilege mode

and normal mode and how to configure router interface and how to save this configuration to
flash memory or permanent memory.

This commands includes
• Configuring the Router commands
• General Commands to configure network
• Privileged Mode commands of a router 
• Router Processes & Statistics
• IP Commands
• Other IP Commands e.g. show ip route etc.

```
## Program:
```
Developed By:SAIRAM V
Reg No: 212225230237 
Client:
import socket
from pythonping import ping

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
print("Server listening on port 8000...")

c, addr = s.accept()
print(f"Connection from {addr}")

while True:
    hostname = c.recv(1024).decode().strip()
    if not hostname: 
        break
    try:
        response = ping(hostname, verbose=False, count=1)
        c.send(str(response).encode())
    except socket.gaierror:
        c.send("Host not found".encode())
    except Exception as e:
        c.send(f"Error: {str(e)}".encode())

c.close()
s.close()

Server:
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter the website you want to ping: ")
    s.send(ip.encode())
    print(s.recv(1024).decode())

```
## Output
<img width="1531" height="274" alt="image" src="https://github.com/user-attachments/assets/fa845623-4a51-45e7-9416-055108436574" />

## Result
Thus Execution of Network commands Performed 
