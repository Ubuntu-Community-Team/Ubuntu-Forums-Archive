---
title: "NetworkManager Applet 0.7.0 problem"
date: 2008-11-23
forum: General Help
---

### Post by AnoPoli on 2008-11-23
Hi all out there!!!
I'm using Ubuntu 8.10 final release since the day it was out.
When i was using the beta of Ubuntu 8.10 i had the same problem.
The problem is that NetworkManager Applet 0.7.0 "forgets" all the settings i'm making to my ethernet cards ( i need static ip's) and falls back to dhcp after a shutdown or reboot. Logout does not seem to affect the settings. To make things clear i have to tell you that the installation was a clear one, from the start with format. Right now i'm using the root account (hoping it would be helped things out), but the same problem was present with the plain user account. I have 2 ethernet "cards" of the same branch (Realtek), the one is onboard and the other is in a pci slot.
Both cards works perfectly in my Debian 4.0r5 installation. Also my floppy drive works perfect in my Debian 4.0r5, while in Ubuntu refuses to work.
The drive some times stays all the time with the led lid and refuses to work, and some times is totally absend.
Thanks in advance!!!
I'm sorry for any grammar or spell errors, i' ve never studied english.
I'm from Hellas and i only studied some French in school, 2 and a half decades ago. I can speak and write VERY GOOD Hellenic though :).

---

### Post by dexter on 2008-11-23
I had similar problems. I have 2 ethernet connectors in my computer. With 8.04 this worked reasonably well with networkmanager. Both were set to dhcp with a manually configured dns server (my router freaks out once in a while so i use the one from my isp). 

With 8.10 however the two connections are a real mess when managed with the network manager, Most of the time i didn't even had a connection to the outside world, could not ping anything. When reconfiguring the networkmanager everything worked again for half an hour or until i rebooted.

After that i decided to remove the whole networkmanager, configure everything myself using the configuration files (/etc/network/interfaces) and everything has been working like a charm since then :).

---

### Post by AnoPoli on 2008-11-23
> **dexter said:**
> I had similar problems. I have 2 ethernet connectors in my computer. With 8.04 this worked reasonably well with networkmanager. Both were set to dhcp with a manually configured dns server (my router freaks out once in a while so i use the one from my isp). 

With 8.10 however the two connections are a real mess when managed with the network manager, Most of the time i didn't even had a connection to the outside world, could not ping anything. When reconfiguring the networkmanager everything worked again for half an hour or until i rebooted.

After that i decided to remove the whole networkmanager, configure everything myself using the configuration files (/etc/network/interfaces) and everything has been working like a charm since then :).

Thank you very much dexter, now at least know that i'm not the only one.
I've had the same idea about removing networkmanager but i have to wait till my aptoncd gets finished. I'm collecting the packages for my girlfriend and aptoncd gets confused sometimes if you remove or manually install packages. I will try it someday soon...

---

### Post by mdeveaux on 2009-04-25
I had a similar problem: I could no longer ssh into the box from the internet after upgrading to 8.10 (from  8.04) .  I could still connect to the machine via the LAN, just not from the other side of the router.  Also the machine would not talk to any box on the internet.

After some browsing I this post gave me a clue:
[http://www.linuxquestions.org/questions/linux-networking-3/etcinit.dnetworking-restart-errors-637610/]("http://www.linuxquestions.org/questions/linux-networking-3/etcinit.dnetworking-restart-errors-637610/")


First I used the users-admin to give my user priviledges to "Connect to wireless and ethernet networks" using the iLO desktop my box has (not sure if this was strickly required).

Secondly I removed the gateway statement from eth1 and added network and broadcast lines to both eth0 and eth1.  I appears it get confused if you have two gateway lines in /etc/network/interfaces.

```

sudo nano /etc/network/interfaces

```

```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.1.11
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

gateway 192.168.1.1

auto eth1
iface eth1 inet static
address 192.168.1.12
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255

```

then I ran 
```

sudo /etc/init.d/networking restart

```

---

### Post by AnoPoli on 2009-08-24
The problem no longer exists to my fresh installation
of Ubuntu 9.04.
Everything seems to obey as expected.:lolflag:

---

