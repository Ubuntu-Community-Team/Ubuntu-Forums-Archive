---
title: "sudo apt-get update problem"
date: 2009-05-03
forum: Installation &amp; Upgrades
---

### Post by David801644 on 2009-05-03
Hi,

I have just started with Ubuntu. :)

My firefox has a connection to the net, through a hardware router managing my adsl line. Its setup to give the computers in the internal network a IP and DHCP service.

From the terminal:

david@Ubuntu1:~$ sudo apt-get update
[sudo] password for david: 
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty/main Translation-en_ZA
  Could not connect to 192.168.1.1:8080 (192.168.1.1), connection timed out
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty/restricted Translation-en_ZA
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty/universe Translation-en_ZA
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty/multiverse Translation-en_ZA
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty-updates Release.gpg
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty-updates/main Translation-en_ZA
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty-updates/restricted Translation-en_ZA
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty-updates/universe Translation-en_ZA
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty-updates/multiverse Translation-en_ZA
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty-security Release.gpg
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty-security/main Translation-en_ZA
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty-security/restricted Translation-en_ZA
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty-security/universe Translation-en_ZA
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty-security/multiverse Translation-en_ZA
  Unable to connect to 192.168.1.1 8080:
Err [http://ubuntu.mirror.ac.za](http://ubuntu.mirror.ac.za) jaunty Release.gpg
  Unable to connect to 192.168.1.1 8080:
Reading package lists... Done               
W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty/Release.gpg](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty/Release.gpg)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty/main/i18n/Translation-en_ZA.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty/main/i18n/Translation-en_ZA.bz2)  Could not connect to 192.168.1.1:8080 (192.168.1.1), connection timed out

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty/restricted/i18n/Translation-en_ZA.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty/restricted/i18n/Translation-en_ZA.bz2)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty/universe/i18n/Translation-en_ZA.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty/universe/i18n/Translation-en_ZA.bz2)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty/multiverse/i18n/Translation-en_ZA.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty/multiverse/i18n/Translation-en_ZA.bz2)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-updates/Release.gpg](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-updates/Release.gpg)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-updates/main/i18n/Translation-en_ZA.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-updates/main/i18n/Translation-en_ZA.bz2)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-updates/restricted/i18n/Translation-en_ZA.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-updates/restricted/i18n/Translation-en_ZA.bz2)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-updates/universe/i18n/Translation-en_ZA.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-updates/universe/i18n/Translation-en_ZA.bz2)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-updates/multiverse/i18n/Translation-en_ZA.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-updates/multiverse/i18n/Translation-en_ZA.bz2)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-security/Release.gpg](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-security/Release.gpg)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-security/main/i18n/Translation-en_ZA.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-security/main/i18n/Translation-en_ZA.bz2)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-security/restricted/i18n/Translation-en_ZA.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-security/restricted/i18n/Translation-en_ZA.bz2)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-security/universe/i18n/Translation-en_ZA.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-security/universe/i18n/Translation-en_ZA.bz2)  Unable to connect to 192.168.1.1 8080:

W: Failed to fetch [http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-security/multiverse/i18n/Translation-en_ZA.bz2](http://ubuntu.mirror.ac.za/ubuntu-archive/dists/jaunty-security/multiverse/i18n/Translation-en_ZA.bz2)  Unable to connect to 192.168.1.1 8080:

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

:confused:

---

### Post by blackened on 2009-05-03
Open a terminal and post the result of
```
cat /etc/resolv.conf
```

---

### Post by David801644 on 2009-05-03
Ok, thanks for your reply here are the resaults:

david@Ubuntu1:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
david@Ubuntu1:~$ 

Looks like its using the internal router. Is that bad?

---

### Post by blackened on 2009-05-03
> **David801644 said:**
> Ok, thanks for your reply here are the resaults:

david@Ubuntu1:~$ cat /etc/resolv.conf
# Generated by NetworkManager
nameserver 192.168.1.1
david@Ubuntu1:~$ 

Looks like its using the internal router. Is that bad?

Would probably be better to use your ISP's DNS servers. You wouldn't have the addresses for those handy would you?

---

### Post by David801644 on 2009-05-03
I'll find em out and place em into the router...

Update:
I use the Mweb as my adsl provider, they sugest that I leave the DNS settings on the router blank? Perhaps they change them from time to time?

Found:
[COLOR=#000000][FONT=verdana]Primary - 196.43.34.190
Alternate - 196.43.46.190

They are in the router now :)
[/FONT][/COLOR]

---

### Post by David801644 on 2009-05-03
Updated the primary dns to 196.43.42.190 its closer to where I live. :)

Restarted & it is working !!!  :)

:guitar:

Big thanks :P

---

### Post by blackened on 2009-05-03
You could always use an ISP independent DNS (something like OpenDNS), though there is some controversy as to their effectiveness. 

My ISP's servers work well enough that it doesn't bother me.

So, apt-get is working for you now then?

**Edit:** Oops, I'm slow. Got sidetracked while reading.

---

### Post by nhaughton on 2009-05-03
I'm having very similar problems. I'm on 7.10 (and apparently stuck there until I can use hardware acceleration with my nvidia card with a newer version). 

Recently  Update Manager started reported errors such as

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/u/udev/libvolume-id0_113-0ubuntu17.2_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/u/udev/libvolume-id0_113-0ubuntu17.2_i386.deb)
  404 Not Found

and today when I tried to install mplayer I got a very similar 


Failed to fetch [http://security.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_1.0~rc1-0ubuntu13.3_i386.deb](http://security.ubuntu.com/ubuntu/pool/multiverse/m/mplayer/mplayer_1.0~rc1-0ubuntu13.3_i386.deb)  404 Not Found


I've tried doing an apt-get update, and I've checked that /etc/resolv.conf uses my ISP's DNS servers:

$ cat /etc/resolv.conf
nameserver 62.24.199.13
nameserver 62.24.199.23

Normal internet access works, well, normally, so the DNS service seems okay.

Is this a consequence of Ubuntu removing support for 7.10 recently? I do hope not. If anyone can throw some light on this I would be grateful.

TIA

Neil Haughton

---

### Post by blackened on 2009-05-03
> **nhaughton said:**
> Is this a consequence of Ubuntu removing support for 7.10 recently? I do hope not. If anyone can throw some light on this I would be grateful.

TIA

Neil Haughton

Unfortunately, that looks to be it.

---

### Post by David801644 on 2009-05-03
Humm, it does sound similar. 

My internet would also work through firefox, however if I changed the network proxy to manual rather than direct it would also stop working. 

Before updating my DNS of couse. :)

---

### Post by blackened on 2009-05-03
> **David801644 said:**
> Humm, it does sound similar. 

My internet would also work through firefox, however if I changed the network proxy to manual rather than direct it would also stop working. 

Before updating my DNS of couse. :)

What you're describing is normal behavior: if you tell Firefox to connect through a proxy, but then don't provide any information about that proxy, then it won't know the route to rake to get where it needs to go.

nhaughton's problem is that the resource simply does not exist anymore because the support period for 7.10 has ended.

---

