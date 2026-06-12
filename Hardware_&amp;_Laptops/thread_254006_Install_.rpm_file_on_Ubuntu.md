---
title: "Install .rpm file on Ubuntu"
date: 2006-09-09
forum: Hardware &amp; Laptops
---

### Post by jadhav333 on 2006-09-09
how can i install  .rpm files on Ubuntu 6.06 ?

somebody suggested to use an Alien rpm to deb converter. but that program is itself an .rpm file.

Pls advise

---

### Post by Anonii on 2006-09-09
> **jadhav333 said:**
> how can i install  .rpm files on Ubuntu 6.06 ?

somebody suggested to use an Alien rpm to deb converter. but that program is itself an .rpm file.

Pls advise
First of all, nearly everything that is in .rpm is on source code too, which is easily installed in Ubuntu.

But, why do you want to install a stupid .rpm? You can use the APT package manager which is both easy and fast. Which program are you trying to install?

---

### Post by linuxusr50 on 2006-09-09
Try:
```
sudo apt-get install alien
```

Be sure to read
```
man alien
```

The command you will need is
```
alien -i package.rpm
```

---

### Post by jadhav333 on 2006-09-09
ANONII: i would like to install that stupid small .rpm because it is the only file made available by my ISP which will enable my linux machine to access the internet. and they have made it available in .rpm format only.


Linuxusr50:
apt-get should work. but can anyone confirm whether it **gets** from the Ubuntu CD or from the internet. Because if it does from the Internet, I donot have acces to the Internet on my linux box. Thatis the reason why the stupid .rpm is required to be installed in the first place. 

Its a vicious circle. :)

---

### Post by Anonii on 2006-09-09
I doubt that alien can get installed from the CD, but if you do have a dual boot and can switch between them, change files/folders, etc.
You can go here from the second OS:
[http://packages.ubuntu.com/dapper/admin/alien](http://packages.ubuntu.com/dapper/admin/alien)
download the .deb and all its dependecies, give them to Ubuntu, and install them using:

_sudo dpkg -i <package_name>.deb_

---

### Post by linuxusr50 on 2006-09-09
> Linuxusr50:
apt-get should work. but can anyone confirm whether it gets from the Ubuntu CD or from the internet.

This would be in the the ubuntu repositories and not included on the disto cd.

---

### Post by andb on 2006-09-09
Im curious about the underlying problem- why is the code needed to connect to internet? I dont like using programs when they arent neccesary... is there some way to connect to the isp without this? What functionality is the program the isp gave you providing?

---

### Post by jadhav333 on 2006-09-09
I have a shared broadband connection provided by the ISP. They provide the drivers (RASPPPOE.inf) necessary to install the **PPP o**ver **E**thernet Protocol.

---

### Post by tommcd on 2006-09-10
I use verizon DSL over PPPoE. You should not need any special software. Just configure PPPoE in ubuntu by typing:
sudo pppoeconf
in terminal. Answer the questions (you can give default 'yes' to all). Provide you username and password when prompted (backspace out the words 'username' and 'password' first). And you're done. When you boot next time just type:
pon dsl-provider
to connect ater booting.
Hope this helps.

---

### Post by Daniel15 on 2006-09-10
Also, once you run pppoeconf, to check that the connection was successful, type in 'plog'. You should get output similar to:
```

Sep 10 21:04:46 server1 pppd[9427]: Using interface ppp0
Sep 10 21:04:46 server1 pppd[9427]: Connect: ppp0 <--> eth1
Sep 10 21:04:47 server1 pppd[9427]: PAP authentication succeeded
Sep 10 21:04:47 server1 pppd[9427]: peer from calling number 00:90:1A:A0:54:BA authorized
Sep 10 21:04:47 server1 pppd[9427]: local  IP address xxx.xxx.xxx.xxx
Sep 10 21:04:47 server1 pppd[9427]: remote IP address 202.7.162.174
Sep 10 21:04:47 server1 pppd[9427]: primary   DNS address 203.12.160.35
Sep 10 21:04:47 server1 pppd[9427]: secondary DNS address 203.12.160.36

```
If there's no output, then try running ```
cat /var/log/messages | grep ppp
``` instead (the output of plog seems to disspear after a while...)

>  When you boot next time just type
I believe that pppoeconf sets up the configuration so it connects automatically on startup.

---

### Post by tommcd on 2006-09-10
Yes, it is supposed to. On my system, sometimes it does, sometimes it doesn't. I don't know why. Here is my /etc/ppp/peers/dsl-provider:

# Minimalistic default options file for DSL/PPPoE connections

noipdefault
defaultroute
replacedefaultroute
hide-password
#lcp-echo-interval 30
#lcp-echo-failure 4
noauth
persist
#mtu 1492
usepeerdns
plugin rp-pppoe.so eth0
user "EDITED"

 as near as I can tell, it is in order.
If it don't connect on boot I just use 'pon dsl-provider'.

---

### Post by Daniel15 on 2006-09-10
Well, mine looks a bit like this:
```

#...

# The following two options should work fine for most DSL users.

# Assumes that your IP address is allocated dynamically
# by your DSL provider...
noipdefault
# Try to get the name server addresses from the ISP.
usepeerdns
# Use this connection as the default route.
# Comment out if you already have the correct default route installed.
defaultroute

#...


hide-password
lcp-echo-interval 20
lcp-echo-failure 3
# Override any connect script that may have been set in /etc/ppp/options.
connect /bin/true
noauth
persist
maxfail 0
mtu 1492

# RFC 2516, paragraph 7 mandates that the following options MUST NOT be
# requested and MUST be rejected if requested by the peer:
# Address-and-Control-Field-Compression (ACFC)
noaccomp
# Asynchronous-Control-Character-Map (ACCM)
default-asyncmap

plugin rp-pppoe.so eth1

replacedefaultroute
user "**********@l2tp.tpg.com.au"

```
*(I removed some useless stuff like extra comments from the top of it)*

I suppose this bit in **/etc/network/interfaces** is what makes it connect automatically?:
```

auto dsl-provider
iface dsl-provider inet ppp
provider dsl-provider

```
[/code]

---

### Post by tommcd on 2006-09-11
Daniel, how did you get your /etc/ppp/peers/dsl-provider file to look like that? Did you edit it manually? or just use pppoeconf? Mine is similar, but yours has extra stuff. 
My /etc/network/interfaces has those same 3 lines also.

---

### Post by Daniel15 on 2006-09-22
It was all done via pppoeconf, the only thing I did was add ```
maxfail 0
``` so it would try an unlimited number of times

Oh, I just remembered now: I had to format my server, and I installed Debian the last time I formatted (mainly due to the [Linux-Vserver](http://www.linux-vserver.org/) packages). Hence, that configuration was created using the Debian pppoeconf. I'm not sure if there's any difference between the Debian and Ubuntu versions, though.

---

