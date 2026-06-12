---
title: "iPhone as GPSD device"
date: 2010-04-22
forum: Hardware
---

### Post by gandhioftherillo on 2010-04-22
Using a Python scipt by balint of Spench.net I can set my iPhone as a gpsd device (using mobile Safari and the tether connection)

```
ryank@kayleeslaptop:~$ sudo python iPhone-gpsd.py
Current directory: /home/ryank
gpsd: Can't bind to port 2947
gpsd: Maybe gpsd is already running!
gpsd: Can't bind to port 2947
gpsd: Maybe gpsd is already running!
GPSd running
Added  /dev/pts/1
HTTP Server running...
Ryan-Kochs-iPhone.local - - [22/Apr/2010 10:54:14] "POST / HTTP/1.1" 200 -
Received 1 updates:
35.21156006666667,-101.86819670000001,47.42163354976343,1271951613442
$GPRMC,105333.44,A,3512.693604,N,10152.091802,W,,,220410,,,A*40


```
It sets the device as /dev/pts/1 but GPSDrive (and any other program for that matter) shows that there is not GPS...

Here's a link to the site:
[http://spench.net/drupal/software/iphone-gps]("http://spench.net/drupal/software/iphone-gps")

Any ideas?

Thanks in advance.

---

### Post by gandhioftherillo on 2010-04-24
Make sure your iPhone's autolock is shut off!

Save iPhone-gpsd.py and index.html to you home folder... get them here:
[http://spench.net/drupal/software/iphone-gps](http://spench.net/drupal/software/iphone-gps) (Download at the bottom of the page)

Install the following packages:
gpsd
gpsd-clients

Run
```
sudo dpkg-reconfigure gpsd
```
and select "NO" at both prompts (this prevents gpsd from auto-running when a usb is connected)

Run
```
sudo /etc/init.d/gpsd stop
sudo /etc/init.d/udev reload
```

Connect your iPhone to your computer (WiFi or tethering)
Find your computers ip on the network (I use tethering so the ip is 192.168.20.2)
run
```
sudo python iPhone-gpsd.py
```
Go to your computers ip address in Mobile Safari (ex. 192.168.20.2)
Click "Enable" on that page

You iPhone should not be an external GPS!

Thanks to balint from spench.net for developing this and working with me so much to get this working correctly on Ubuntu!

---

### Post by kmel83 on 2010-11-30
I can't have the iphone work with the script. Everytime I get this:
test@test:~$ sudo python iPhone-gpsd.py
Current directory: /home/test
Traceback (most recent call last):
  File "iPhone-gpsd.py", line 365, in <module>
    m.main()
  File "iPhone-gpsd.py", line 336, in main
    self.serverWeb = HTTPServer(('', 80), MyHandler)
  File "/usr/lib/python2.6/SocketServer.py", line 402, in __init__
    self.server_bind()
  File "/usr/lib/python2.6/BaseHTTPServer.py", line 108, in server_bind
    SocketServer.TCPServer.server_bind(self)
  File "/usr/lib/python2.6/SocketServer.py", line 413, in server_bind
    self.socket.bind(self.server_address)
  File "<string>", line 1, in bind
socket.error: [Errno 98] Address already in use

I am trying to get this working with tethering. I use my iphone as a modem with umux2007.
If anyone has a solution it will be great!
Xavier.

---

### Post by carl.davis on 2012-11-27
> **kmel83 said:**
> I can't have the iphone work with the script. Everytime I get this:
test@test:~$ sudo python iPhone-gpsd.py
Current directory: /home/test
Traceback (most recent call last):
  File "iPhone-gpsd.py", line 365, in <module>
    m.main()
  File "iPhone-gpsd.py", line 336, in main
    self.serverWeb = HTTPServer(('', 80), MyHandler)
  File "/usr/lib/python2.6/SocketServer.py", line 402, in __init__
    self.server_bind()
  File "/usr/lib/python2.6/BaseHTTPServer.py", line 108, in server_bind
    SocketServer.TCPServer.server_bind(self)
  File "/usr/lib/python2.6/SocketServer.py", line 413, in server_bind
    self.socket.bind(self.server_address)
  File "<string>", line 1, in bind
socket.error: [Errno 98] Address already in use

I am trying to get this working with tethering. I use my iphone as a modem with umux2007.
If anyone has a solution it will be great!
Xavier.

Try:
```

sudo /etc/init.d/apache2 stop
sudo python ./iPhone-gpsd.py

```

---

