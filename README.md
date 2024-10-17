NAME : Vimala rani A
REG NO : 212223040240

# 2c.SIMULATING ARP /RARP PROTOCOLS
## AIM
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.
P
## PROGRAM - ARP

CLIENT :

import socket     
s=socket.socket()        
s.bind(('localhost',8000))                 
s.listen(5)                
c,addr=s.accept()                                                     
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};                      
while True:                             
            ip=c.recv(1024).decode()           
            try:                             
                c.send(address[ip].encode())               
            except KeyError:                      
                c.send("Not Found".encode())                     

SERVER :

import socket             
s=socket.socket()                      
s.connect(('localhost',8000))                      
while True:                                 
    ip=input("Enter logical Address : ")                      
    s.send(ip.encode())                          
    print("MAC Address",s.recv(1024).decode())  
    
## OUPUT - ARP    

CILENT : 

![image](https://github.com/user-attachments/assets/561f87e3-e02a-473c-91df-afd630655338)

SERVER :

![image](https://github.com/user-attachments/assets/5d48c42c-b890-4750-b67b-77b7493efd3f)

## PROGRAM - RARP

CLIENT :
import socket        
s=socket.socket()            
s.bind(('localhost',9000))               
s.listen(5)             
c,addr=s.accept()                                                    
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};             
while True:                               
            ip=c.recv(1024).decode()             
            try:                           
                c.send(address[ip].encode())                     
            except KeyError:                 
                c.send("Not Found".encode())                   

SERVER :

import socket              
s=socket.socket()                   
s.connect(('localhost',9000))                    
while True:                                
    ip=input("Enter MAC Address : ")                 
    s.send(ip.encode())                            
    print("Logical Address",s.recv(1024).decode())                

## OUPUT -RARP

CLIENT:

![image](https://github.com/user-attachments/assets/45c133bc-3762-4208-9429-c1ec840a89b2)

SERVER :

![image](https://github.com/user-attachments/assets/a589835e-a333-4d17-8c76-01ac9478a14e)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
