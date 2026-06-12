---
title: "HP Laserjet P1005 on Ubuntu 8.04 LTS"
date: 2009-10-08
forum: Hardware
---

### Post by faller69 on 2009-10-08
Hi, does anyone out there have a _**HP Laserjet P1005**_ on Ubuntu that is working reliably and how did you get it there.  Have been fighting with this with Debian 5.0.3 Lenny and getting nowhere.  (Lots of advice from people who have other printers!)  So if somebody here actually has this working on Ubuntu 8.04 or above (just installed 8.04 for long term support) I would be deeply grateful for any and all help getting this working.

---

### Post by ajgreeny on 2009-10-08
See this page for more information.  You may need a more up to date version of hplip, or need the driver plugin mentioned there.

[http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1005.html](http://hplipopensource.com/hplip-web/models/laserjet/hp_laserjet_p1005.html)

---

### Post by faller69 on 2009-10-08
Yeah thanks ajgreeny but I've been there done that with all kinds of sites (HPlip.sourceforge.net, localhost:631/printers HP website et.al.)  What I'm really looking for is the word from someone who has one working on a ubuntu desktop.

---

### Post by sertirion on 2009-10-13
> **faller69 said:**
> Hi, does anyone out there have a _**HP Laserjet P1005**_ on Ubuntu that is working reliably and how did you get it there. 

I bought this printer a few days ago and it seems working well on Ubuntu 8.04.2.

About installing it, I just installed the package hplip-gui

```
sudo apt-get install hplip-gui

```and, after launching this gui tool, I setup the device via the **hp-setup** option (this script seems to download and install a binary driver from the HP server), and it worked.

---

### Post by Sénal on 2009-12-20
> **sertirion said:**
> I bought this printer a few days ago and it seems working well on Ubuntu 8.04.2.

About installing it, I just installed the package hplip-gui

```
sudo apt-get install hplip-gui

```and, after launching this gui tool, I setup the device via the **hp-setup** option (this script seems to download and install a binary driver from the HP server), and it worked.
:)

---

