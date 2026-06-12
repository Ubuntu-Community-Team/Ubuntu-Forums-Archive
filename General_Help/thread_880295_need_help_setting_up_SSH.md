---
title: "need help setting up SSH"
date: 2008-08-04
forum: General Help
---

### Post by malfist on 2008-08-04
I recently set up ssh and nxserver, and I can connect to my machine using 127.0.0.1, however I can't connect to it using my router's IP and it's set up for port forwarding.

I know it can be done, I know it's fairly easy, but I couldn't find anything with google. Someone care to help?

---

### Post by cariboo on 2008-08-04
The easiest way to do what you are trying, is to set up a static ip address on the computer you are trying to access. To do this edit /etc/network/interfaces to look like this:

```
# The primary network interface
auto eth0
iface eth0 inet static
address 192.168.1.200
netmask 255.255.255.0
broadcast 192.168.1.255
gateway 192.168.1.1
```

Of course you will have to change the address line to match your network. I suggest using an ip address above what your router assigns by dhcp. Change the address of gateway to match the address you use to sccess your router's web interface.

Once you have done the above you can now open uo the management interface on your router and set port forwarding for port 21 from the computer you just set the static ip on to the outside world. If you're not clear on where to go for port forwarding on your router, check the documentation that came on the installation cd for your router because all the manufacturers do it different ways.

Jim

---

### Post by malfist on 2008-08-04
My box is set to 192.168.1.102, and it never changes. Likewise, I have broadband and a static IP for the router. SSH is actually using port 22, the defualt, and port forwarding is setup with the router, however, I get connection timeout when I try to connect.

---

### Post by 3rods on 2008-08-04
Are you having problems with NXMachine or Both?


How did you setup nx? 

Install client, then node, then server in that order or it won't work.

---

### Post by malfist on 2008-08-05
Both, I set up NX in that order and nxserver --status returns the proper responce, I can connected to NX and SSH through localhost, but no other way.

They strage thing is, I've just reformatted, and before I reformatted, I installed NX in the exact same way without any problems...

---

### Post by 3rods on 2008-08-09
It's really hard to say without seeing your router settings, et al. 

Have you tried telnet to the port from outside of your network? See if it responds.

Check this out for testing with SSH and telnet:

[http://www.javassh.org/space/Java+WebStart]("http://www.javassh.org/space/Java+WebStart")

web-based SSH & telnet. You need java though.

---

### Post by malfist on 2008-08-09
It was the router, I had the wrong ip, off by 1.

---

