---
title: "[SOLVED] SSH problems"
date: 2008-08-22
forum: General Help
---

### Post by Knuffle on 2008-08-22
I have looked everywhere for help and am not finding it. I am a novice when it comes to how the internet works (ip adresses and stuff) and a novice to Linux. I am trying to remotely control my server which uses Ubuntu Server with my laptop which runs Ubuntu. I have no idea what I am doing, and any help will be greatly appreciated. Thanks! :)

---

### Post by jerome1232 on 2008-08-22
Are you doing this over your LAN (local connections) or over a WAN connection (the internet)

What are you trying right now that's not working?

Is a firewall setup on the server?

If your connecting over the internet is the server behind a router?
If yes do you know what your public ip is (don't post it)?
Is the router set up to forward the necessary port? 22 by default

Can you post what commands your are entering and the error your receiving?

Did you install openssh-server on the server?

Those are all I can think of off the bat.

---

### Post by Knuffle on 2008-08-22
I am trying to access it from the internet with my wireless laptop. The server is plugged into a router with an ethernet cord. I don't know if anything has firewalls. I just installed the Ubuntu stuff and havn't set anything special up. I have no idea how to find or work with ip stuff. I don't even know exactly what their used for. The error i keep receiving is "Name or service not known"

P.S. I changed the port thing to 2222 because someone said that would help.

---

### Post by jerome1232 on 2008-08-23
Ok awesome, I'm assuming you did install openssh-server on the server since you said you changed the default port to 2222.

On the servers end we need to figure out a few things
a: it's private ip
b: your routers ip
c: The public ip assigned by your modem to the router (yes router's have 2 ip's one public one private)

a: On the server type ifconfig to get it's private ip it'll look something like this (bold is what you are interested in.) In mine eth1 is the active device (yours will more than likely be eth0 and my ip address is 192.168.1.4 we will need it later
```
jeremy@desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:8d:7b:7f:9b  
          inet6 addr: fe80::250:8dff:fe7b:7f9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:468 (468.0 B)
          Interrupt:21 Base address:0xdd00 

eth1      Link encap:Ethernet  HWaddr 00:11:50:b4:2c:2d  
          **inet addr:192.168.1.4**  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::211:50ff:feb4:2c2d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27017 errors:4750 dropped:342 overruns:0 frame:4467
          TX packets:27834 errors:551 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:31144312 (29.7 MB)  TX bytes:1824101190 (1.6 GB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1316 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1316 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:65800 (64.2 KB)  TX bytes:65800 (64.2 KB)
```

b: If you type "route" usually the last thing on the list will be default and it will have an ip address next to it (ok mines not an ip address but I have a special setup, instead of router.home.lan yours will probably say 192.168.1.1 or 192.168.1.254)
```
jeremy@desktop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
**default         router.home.lan 0.0.0.0         UG    0      0        0 **eth1

```

Now open you favorite web brower and point it to what was under default, in my case router.home.lan

This should ask you to login, if you have no idea what your login is, google your router model or post it here and I can figure out it's defaults. Once in there we can set it up to forward port 2222 to your server and figure out your public ip address.

---

### Post by Loaded.len on 2008-08-23
That is, providing the necessary login/password is known to get INTO the router's web-based setup.

---

### Post by jerome1232 on 2008-08-23
Well I say that cause if he didn't configure it then it's got a default... and defaults can be found with 1 or 3 google searches. But yeah your right. Provided the defaults are known.

second edit: I want to make sure we are clear on this, is the laptop connected wirelessly to the same router? Because if it is,we don't have to mess with the router.

---

### Post by Knuffle on 2008-08-23
Both computers are hooked up to the same internet connection and router. Ill see if this works. Thanks guys! :)

---

### Post by jerome1232 on 2008-08-23
Okay if they are connected to the same router, you don't have to forward ports. And by the way if that server is behind a router, there is zero benefit of changing the port from 22 to 2222.

Even if it was open to the internet, just use not easy to guess usernames and strong passwords and you'll be fine.

All you need is the private ip of the router, then you would connect to it like this:

```
ssh loginname@ip.of.the.router -p 2222
```

---

### Post by Knuffle on 2008-08-23
Ok, I still have no idea what I'm doing. I am a total newbie when it comes to networking.

---

### Post by jerome1232 on 2008-08-23
post the output of the command ifconfig here, do that on the server.

---

### Post by Knuffle on 2008-08-25
eth0      Link encap:Ethernet  HWaddr 00:e0:b8:4a:8a:66  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fe4a:8a66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:253584 (247.6 KB)  TX bytes:1018 (1018.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




I also don't know how to find my private ip or how to change my ssh port thing back to port 22. I really appreciate that you guys are trying to help. It must be frustrating.

---

### Post by jerome1232 on 2008-08-25
> **Knuffle said:**
> eth0      Link encap:Ethernet  HWaddr 00:e0:b8:4a:8a:66  
          inet addr:**192.168.0.2**  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:b8ff:fe4a:8a66/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:787 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:253584 (247.6 KB)  TX bytes:1018 (1018.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)




I also don't know how to find my private ip or how to change my ssh port thing back to port 22. I really appreciate that you guys are trying to help. It must be frustrating.

No problem the part in bold is your servers private IP, so to login in via ssh, replace user with a user that can login to the server. You can leave it at port 2222 it's not going to harm anything.

```
ssh user@192.168.0.2 -p 2222
```

---

### Post by Catalyst2Death on 2008-08-25
I think this link would be useful:
[http://www.sitepoint.com/article/fire-up-linux-server/11](http://www.sitepoint.com/article/fire-up-linux-server/11)

You want to run the ssh protocol to do most of your administration (obviously) but setting up and configuring ssh can be tricky sometimes.  

First you should set up and make sure you can login on the local network. Do this by connecting to your wireless router and then ssh into the local ip:

ssh [email]UsernameOnServer@192.168.pref[/email]ixForServer

then you'll know that the server and client are configured correctly.

setting up ssh:
[http://www.linuxhelp.net/guides/ssh/](http://www.linuxhelp.net/guides/ssh/)
[http://www.mines.edu/~gmurray/HowTo/sshNotes.html](http://www.mines.edu/~gmurray/HowTo/sshNotes.html)

after you get this working, then you can tackle connecting from outside connections, which will may be limited by your router.

---

### Post by Knuffle on 2008-08-26
Yes! Thank you. Now, the last things that I am hoping to be able to do: Transfer files to my server and access it across the internet while im on vacations. How would I do that? Thanks again!

---

### Post by jerome1232 on 2008-08-26
I would suggest taking a look at those links Catalyst2Death gave you and read up on ssh and ssh security.

I'm going to emphasize on reading up on ssh security, you don't want some script kiddy brute forcing your password with a dictionary attack and taking over your server do you? 

You would probably want to take a look at [http://portforward.com/](http://portforward.com/) to learn how to forward port 2222 to your server.


If you are going to make ssh service available over the internet I would use hard to guess user names and strong passwords on your server. 

My server gets it's ssh service attacked ALOT, one day it got hit for an entire day by one ip guessing usernames and passwords, (came out to be a 122 kb log from that one attacker, that was one of three that tried to break in) I use strong unpronouncable passwords and usernames that wouldn't be in a dictionary, I also force dsa key authentication (I'm sure one of those guides talk about that) so passwords actually can't be guessed.

Take a look at those guides and if you have more questions just ask :)

as for transfering files, I would look at sshfs, it lets you mount directories on the server, onto your laptop and treat them as if they were just regular local directories.
to install it
```
sudo apt-get install sshfs
```

---

### Post by Loaded.len on 2008-08-26
I 2nd what jerome1232 says. My logs periodically show someone hammering away at certain ports for hours on end. I'm sure that what saves me is that my passwords are very cryptic and change often. Use a password that's at least 8 characters in length, has a mix of upper and lower case, numbers and special characters. And even then, stay away from usernames like "admin" or "bob"

---

### Post by Knuffle on 2008-08-26
Thanks a ton. I have finally solved my problem.

---

