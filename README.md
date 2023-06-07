# EX-10 APPLICATION USING TCP SOCKETS - FILE TRANSFER PROGRAM

### DATE :

### AIM :
## To write a python program for creating Chat using TCP Sockets Links

### ALGORITHM :
## Client:
## 1.Import the necessary modules in python
## 2.Create a socket connection to using the socket module.
## 3.Send message to the client and receive the message from the client using the Socket module in server
## 4.Send and receive the message using the send function in socket.


### PROGRAM :
### CLIENT:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
 while True:
  print('receiving data...')
  data = s.recv(1024)
  print('data=%s', (data))
  if not data:
    break
  f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```
### SERVER:
```
import socket

port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port))
s.listen(5)

while True:
    conn, addr = s.accept()
    data = conn.recv(1024)
    print('Server received', repr(data))
    filename = 'myfile.txt'  # Replace 'path/to' with the actual path to the file
    try:
        with open(filename, 'rb') as f:
            l = f.read(1024)
            while l:
                conn.send(l)
                print('Sent', repr(l))
                l = f.read(1024)
        print('Done sending')
    except FileNotFoundError:
        print(f'File {filename} not found.')
    
    conn.send('Thank you for connecting'.encode())
    conn.close()
```
### CLIENT OUTPUT:
![image](https://github.com/tsanjaithirumal/EX-10/assets/119393916/d284260c-64c8-4624-a0f4-17bf2d04328d)

### SERVER OUTPUT :
![image](https://github.com/tsanjaithirumal/EX-10/assets/119393916/800e484d-95cf-4c5e-be48-6995fe465a0d)

### RESULT :
## Thus, the python program for creating File Transfer using TCP Sockets Links was successfully created and executed.
