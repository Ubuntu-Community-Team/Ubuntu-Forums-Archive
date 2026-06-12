---
title: "Satellite u400-133 install problem"
date: 2008-09-26
forum: Hardware
---

### Post by ejardim on 2008-09-26
Hi,

I'm having problems installing ubuntu 8.04.1 amd64 desktop. During install my x11 does not work, even if I set to "safe visual mode" or vga=normal. Can someone help on this one ?

EJ

---

### Post by bsmash on 2008-10-01
Hey,

I'm having the same problem. The graphic card is an Mobile Intel® GMA 4500MHD. And the screen size is 13.3".

It's possible to install ubuntu, or it's incompatible and i have to way for an upgrade?

Thanks

---

### Post by agustin.g on 2008-10-02
Exactly the same here, doesn't work with fedora either. Anyone know of something we could do?

cheers

Specs:
Toshiba Portégé M800
Intel GM45 Chipset
Intel 4500MHD integrated graphics

---

### Post by justynbutler on 2008-10-07
Same problem here - X displays nothing on a Sony SR19XN with Intel GMA 4500MHD graphics.
Tried with Ubuntu 8.04.1, 8.10 Beta and Fedora 10 Alpha.

X starts fine according to the log (press control-alt-f1 to switch to a virtual terminal), and you can hear the ubuntu startup sound.

---

### Post by cark on 2008-10-12
Hi,
I have the same problem. Does anyone know how to solve it?

Thx

---

### Post by obaino on 2008-10-12
I have the same problem using Toshiba Tecra A10-11M with

Mobile Intel® GMA 4500MHD, up to 1,340 MB total available graphics memory with 3 GB system memory, 16x PCI Express

Couldn't install Ubuntu using the live CD. Installed it using the alternate cd (Ubuntu 8.04.1)

Although I see the initial Ubuntu screen at startup when I have to reach the login screen, everything is scrambled.

---

### Post by vtslimik on 2008-10-20
Any progress on this issue?

---

### Post by sbmuschel on 2008-10-30
Hi I have similar problem. I have Toshiba Portege M800 and whenever I tried to install/boot live CD of any Linux OS the screen just scrambles.

Please help

---

### Post by derekshaw on 2008-12-16
I'm researching a lenovo laptop with the same display adapter.

have you seen this link(last post is "xorg7.4 fixed this issue"):
[http://bbs.archlinux.org/viewtopic.php?pid=451980](http://bbs.archlinux.org/viewtopic.php?pid=451980)

---

### Post by WiFi Ed on 2008-12-16
See this at Launchpad:

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/268615]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-intel/+bug/268615")

I was able to get Ubuntu 8.10 working on a VAIO SR240 with the Intel 4500MHD graphics chip by installing the .deb files attached to one of the posts on the Launchpad thread.

Use at your own risk, of course...

---

### Post by strohmi on 2008-12-30
Hi all,

I've just installed Kubuntu 8.10 (32 Bit) to my brand new Toshiba Portege M800 and did not see any problems. (Didn't check full hardware support so far but graphics and WLANseem to work.)

I only see one problem: after working for some time under KDE (e.g. 20 minutes) the system recognizes a new monitor. Some (20?) dialog boxes are popping up asking to accept or ignore the new monitor and then KDE is restarting. 
(I don't want to mess up this thread. Going to search for this in the forum and start a new thread if I don't find the solution.)

BR
strohmi

---

