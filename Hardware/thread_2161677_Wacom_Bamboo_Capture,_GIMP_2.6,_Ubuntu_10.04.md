---
title: "Wacom Bamboo Capture, GIMP 2.6, Ubuntu 10.04"
date: 2013-07-11
forum: Hardware
---

### Post by Cu Rua on 2013-07-11
I've read the tablet's supposed to work straight out of the box, but I can't get it to do anything! Help!

Tried to configure input devices in GIMP and Inkscape, it shows up as Virtual Core XTEST Pointer, and refuses to give me the full range of options shown in this tutorial: [https://help.ubuntu.com/community/Wacom](https://help.ubuntu.com/community/Wacom) 

Tried to get drivers in terminal, but the connection keeps timing out. Also, Synaptic Package Manager insists I have the most up-to-date version of those drivers anyway. 
```
 rachael@rachael-desktop:~$ uname -r
2.6.32-49-generic 
rachael@rachael-desktop:~$ git clone git://git.code.sf.net/p/linuxwacom/input-wacom linuxwacom-input-wacom
Initialized empty Git repository in /home/rachael/linuxwacom-input-wacom/.git/
git.code.sf.net[0: 216.34.181.155]: errno=Connection timed out
fatal: unable to connect a socket (Connection timed out)

```

Do I need a better version of GIMP? Ubuntu? Drivers?

---

