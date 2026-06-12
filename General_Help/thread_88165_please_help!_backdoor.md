---
title: "please help! backdoor?"
date: 2005-11-09
forum: General Help
---

### Post by blakken on 2005-11-09
I discovered recently this:
slayer@ubuntu:~$ nmap localhost

Starting nmap 3.81 ( [http://www.insecure.org/nmap/](http://www.insecure.org/nmap/) ) at 2005-11-09 22:48 CET
Interesting ports on localhost.localdomain (127.0.0.1):
(The 1657 ports scanned but not shown below are in state: closed)
PORT      STATE SERVICE
22/tcp    open  ssh
25/tcp    open  smtp
631/tcp   open  ipp
32770/tcp open  sometimes-rpc3
32771/tcp open  sometimes-rpc5
32774/tcp open  sometimes-rpc11

Nmap finished: 1 IP address (1 host up) scanned in 0.324 seconds
slayer@ubuntu:~$ sudo netstat -nap | grep 32774
tcp        0      0 0.0.0.0:32774           0.0.0.0:*               LISTEN     8469/konqueror
udp        0      0 0.0.0.0:32774           0.0.0.0:*                          8469/konqueror
slayer@ubuntu:~$ sudo netstat -nap | grep 32771
tcp        0      0 127.0.0.1:32771         0.0.0.0:*               LISTEN     7604/python 
slayer@ubuntu:~$ sudo netstat -nap | grep 32770
tcp        0      0 127.0.0.1:32770         0.0.0.0:*               LISTEN     7600/hpiod  
tcp        0      0 127.0.0.1:57388         127.0.0.1:32770         ESTABLISHED7604/python 
tcp        0      0 127.0.0.1:32770         127.0.0.1:57388         ESTABLISHED7600/hpiod  
how come python is listening tcp port?
how to close those 32770/1/4 ports ?
searching the forum no real answers ,even worst over google ,I checked I don't have portmapper installed!
:confused:

---

### Post by Kyral on 2005-11-09
Localhost.localdomain (127.0.0.1) is also known as the local loopback. It doesn't even connect to the internet. It just loopsback to your computer.

In short, its harmless :P

---

### Post by drgonzo69 on 2005-11-24
I have port 32*** open too here is my 'netstat -ntp' result

tcp 0 0 127.0.0.1:32770 127.0.0.1:37852 ESTABLISHED9089/python
tcp 0 0 127.0.0.1:37852 127.0.0.1:32770 ESTABLISHED9104/python

Because I run eric - a Python QT IDE that uses the ports 32770 37852 for debugging, you probably have something similar. And yes, as one of the replies said, it is a local loopback not an external connection.

---

