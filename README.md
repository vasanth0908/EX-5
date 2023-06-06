IMPLEMENTATION OF REVERSE ADDRESS RESOLUTION PROTOCOL(RARP)
EXP: 5
DATE:05-04-2023
AIM:
To write a python program for implementing Reverse Address Resolution Protocol(RARP).

ALGORITHM:
Client:
Start the program
Using datagram sockets UDP function is established.
Get the MAC address to be converted into IP address.
Send this MAC address to server.
Server returns the IP address to client.
Server:
Start the program.
Server maintains the table in which IP and corresponding MAC addresses are stored.
Read the MAC address which is send by the client.
Map the IP address with its MAC address and return the IP address to client.
PROGRAM:
CLIENT:
import socket
s = socket.socket()
s.bind(("localhost", 8000))
s.listen(5)
c, addr = s.accept()
address={"6A:08:AA:C2":"165.165.80.80","8A:BC:E3:FA":"165.165.79.1"};
while True:
   ip=c.recv(1024).decode()
   try:
       c.send(address[ip].encode())
   except KeyError:
       c.send("Not found".encode())
SERVER:
import socket
s=socket.socket()
s.connect(("localhost", 8000))
while True:
    ip=input("Enter the MAC address:")
     
    s.send(ip.encode())
    print("logical Address",s.recv(1024).decode())
OUTPUT:
![1](https://github.com/vasanth0908/EX-5/assets/122000018/6bc85e1f-bbdb-4d87-9f1c-8c0fe246324b)

![2](https://github.com/vasanth0908/EX-5/assets/122000018/80a9f41c-98f1-4062-a729-0f62116eec5e)

RESULT:
IMPLEMENTATION OF REVERSE ADDRESS RESOLUTION PROTOCOL(RARP) EXECUTED SUCCESSFULLY
