---
title: "haproxy"
date: 2008-09-03
forum: General Help
---

### Post by ksalt on 2008-09-03
Not sure where to post this, but...

I am using hardy (on EC2) and installed haproxy with apt-get, it seems to start up fine. When I check to see if I can get to it on port 80 using telnet and have it transfer to another host, haproxy says it got the the connection, but then immediately closes the connection and the telnet session get the message  a connection refused message...

Any ideas?

global
        maxconn 32000
        ulimit-n 65536

listen application :80
        mode http
        balance roundrobin
        server srv1 "ip-address-here":80

---

### Post by flyjedi on 2009-04-29
I've just done a guide on HAProxy under Ubuntu here:
[http://bluhaloit.wordpress.com/2009/04/29/how-to-quickly-setup-a-load-balanced-high-availability-apache-cluster/](http://bluhaloit.wordpress.com/2009/04/29/how-to-quickly-setup-a-load-balanced-high-availability-apache-cluster/)

---

### Post by smo0th on 2010-05-18
Have you already checked the EC2 firewall?

---

### Post by agarwalpranay on 2010-06-17
Hi, I am using haproxy for the first time.I downloaded the latest version 1.4.7 and then unpacked it.then opened the terminal and wrote the command
$make -f Makefile.bsd REGEX=pcre DEBUG= COPTS.generic="-Os -fomit-frame-pointer -mgnu"
 After which an executable haproxy file was created which I copied to /usr/local/sbin.
then i wrote $sudo make install
then I make a configuration file in /etc/haproxy.cfg which is as follows

global
      maxconn 4096
      pidfile /var/run/haproxy.pid
      daemon

defaults
      mode http
      retries 3
      option redispatch
      maxconn 2000
      contimeout 5000
      clitimeout 50000
      srvtimeout 50000

listen GALAXY 192.168.63.51:8080
      mode http
      cookie GALAXY insert
      balance roundrobin
      option httpclose
      option forwardfor
      stats enable
      stats auth myuser:mypass
      server EARTH 192.168.63.52:7634 cookie GALAXY_SERVER_01 check
      server MOON 192.168.63.53 :7634 cookie GALAXY_SERVER_02 check 


But it's not working it is various kind of errors intially it was showing "cannot bind to socket" so tried changing the port number but didn't help
I also used command like $sudo sysctl  net.ipv4.ip_nonlocal_bind=1  But didn't help.
Please Help!!!

---

### Post by smo0th on 2010-06-17
Hi there agarwalpranay,

Looks like you need to enable haproxy by editing the following file and make sure you have ENABLED=1

$ cat /etc/default/haproxy 
# Set ENABLED to 1 if you want the init script to start haproxy.
ENABLED=1
# Add extra flags here.
#EXTRAOPTS="-de -m 16"

---

