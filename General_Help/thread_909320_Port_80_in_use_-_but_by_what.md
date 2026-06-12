---
title: "Port 80 in use - but by what"
date: 2008-09-03
forum: General Help
---

### Post by Duffy on 2008-09-03
I am trying to run an application called "Sambar Server on Ubuntu 8.04. This is a new install of Ubuntu. When I try to start Sambar, it fails and the error log says something is already using port 80.

So I checked with netstat and nothing shows up as using Port 80.

me@server2:/$ netstat -an --tcp
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN     
tcp        1      1 192.168.1.17:48324      64.233.167.100:80       LAST_ACK   
tcp        1      1 192.168.1.17:46008      212.58.226.20:80        LAST_ACK   
tcp        0      0 192.168.1.17:34316      74.125.12.17:80         ESTABLISHED
tcp        0      0 192.168.1.17:55369      64.233.187.99:80        ESTABLISHED

So I don't understand how to fix this issue. I tried another application, Citadel, and have the same problem. What could be tying up Port 80 and how do I find out?

---

### Post by mkvnmtr on 2008-09-03
I have never checked in Ubuntu but on my Mac port 80 is the standard port for non secure internet connections.

---

### Post by kdwillia on 2008-09-03
Why not open up a web browser and type in [http://localhost](http://localhost)

See what comes up... that will tell you what is using port 80.

---

