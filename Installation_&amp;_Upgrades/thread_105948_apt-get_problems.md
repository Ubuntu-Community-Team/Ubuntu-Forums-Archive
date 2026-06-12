---
title: "apt-get problems"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by campa on 2005-12-19
Hi,

Some days ago I have installed the 5.04, but my apt-get haven't worked.

Seems it cannot reach the repositories, but i can surf they with firefox.
I tried to change the mirror from "it" to "gb" and after to "us", but the error is the same.
stefano@ubuntuCampa:/etc$ sudo apt-get update
Password:
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hoary Release.gpg
  Could not connect to it.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
....

Can you help me ?
Thanks in advance
Stefano

---

### Post by ranf on 2005-12-19
[QUOTE=campa]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[/QUOTE]
I think the 1.0.0.0 in brackets is the IP address your router gives you for archive.ubuntu.com.

It is wrong.

What sort of router is this?

---

### Post by campa on 2005-12-19
Hi, 

it is an adsl simple router...
Do you mean the IP address that others (Web server and so on) see mine ? 

internally the router gives me:
------------- 
eth1   Link encap:Ethernet  HWaddr 00:90:27:36:36:EF
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::290:27ff:fe36:36ef/64 Scope:Link
          ........
But externally, I don't know: how I can control that ?
Have you Some Ideas ?

Thanks in adavance
Stefano

---

### Post by ranf on 2005-12-19
Can you ping the repository server?
```
ping -c 10 archive.ubuntu.com
```

---

### Post by campa on 2005-12-19
Yes,

stefano@ubuntuCampa:~$ ping -c 10 archive.ubuntu.com
PING archive.ubuntu.com (82.211.81.151) 56(84) bytes of data.
64 bytes from archive.ubuntu.com (82.211.81.151): icmp_seq=1 ttl=50 time=36.4 ms
64 bytes from archive.ubuntu.com (82.211.81.151): icmp_seq=2 ttl=50 time=37.1 ms
64 bytes from archive.ubuntu.com (82.211.81.151): icmp_seq=3 ttl=50 time=37.1 ms

Thanks you for your time !
Bye

---

### Post by ranf on 2005-12-19
Now try again:
"sudo apt-get update"

---

### Post by campa on 2005-12-19
Done ... but same problems....

stefano@ubuntuCampa:~$ sudo apt-get update
Password:
Err [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) hoary Release.gpg
  Could not connect to it.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
....

Bye
Stefano

---

### Post by DX 00 on 2005-12-24
I get the same problem when i try "apt-get update" except i can access some of them. I have the same type of router, an adsl wireless router. Could this be the problem? This is what i get when i do sudo apt-get update

Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]time
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release.gpg
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras Release
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/main Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/universe Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/multiverse Packages
Ign [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-extras/restricted Packages
Err [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages
  404 Not Found

---

### Post by DX 00 on 2006-01-25
campa, 

Unfortunately I got some bad news for you and me. I just moved and my new apartment is no longer DSL but Cable. Because of this, I had to buy a new modem and router. As soon as I connected in my new apartment, everything worked fine. I did not change my Ubuntu configurations or anything, I just ran 

apt-get update
apt-get upgrade

and everything worked fine. I really think it was the ADSL modem that was causing the problem unless it's the ISP. I was going through Qwest in Phoenix AZ. I say get another router or modem and try it then but who knows, maybe there is a better solution.

---

