---
title: "Unable to connect usb intuos wacom pen and touch tablet"
date: 2016-07-03
forum: Hardware
---

### Post by fossuvon on 2016-07-03
Hi,

I have a intuos wacom pen and touch tablet, but I can't connect with USB. I've done [https://help.ubuntu.com/community/Wacom/LatestDriver](https://help.ubuntu.com/community/Wacom/LatestDriver) .

Here is some result command on my system (sorry it's in french)

```

herve@grosse-machine:~$ uname -a
Linux grosse-machine 3.13.0-91-generic #138-Ubuntu SMP Fri Jun 24 15:58:13 UTC 2016 i686 i686 i686 GNU/Linux
```

```
herve@grosse-machine:~$ lsusb
Bus 002 Device 003: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 056a:033c Wacom Co., Ltd 
Bus 001 Device 003: ID 1210:25f4 DigiTech 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

```
herve@grosse-machine:~$ xsetwacom --list devices
(no result)
```

Thank's for your help.

---

### Post by mörgæs on 2016-07-03
Which tablet? 

How does it work in a live boot of 16.04?

---

### Post by fossuvon on 2016-07-03
> **mörgæs said:**
> Which tablet? 

it's a intuos art wacom tablet, this : [https://www.wacom.com/en-us/products/pen-tablets/intuos-art](https://www.wacom.com/en-us/products/pen-tablets/intuos-art)
> **mörgæs said:**
> How does it work in a live boot of 16.04?
Sorry, I doesn't understand your question. How I do that ?

Thanks for your help.

---

### Post by mörgæs on 2016-07-04
[http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install](http://www.ubuntu.com/download/desktop/try-ubuntu-before-you-install)

---

### Post by fossuvon on 2016-07-04
I doesn't understand, but that doesn't work on my computer.

I've download 
ubuntu-16.04-desktop-amd64.iso and install it on usb key with "Créateur de disque de démarrage" - it's in my kubuntu -, then I reboot, and my computer said :

Missing parameter in configuration file keyword path
gfx boot.c32 not a com 32 R image

---

### Post by mörgæs on 2016-07-04
[http://ubuntuforums.org/showthread.php?t=2249701](http://ubuntuforums.org/showthread.php?t=2249701)

---

### Post by fossuvon on 2016-07-04
Ir's work !

... but not my tablet.

When I am in the usb-ubuntu, I launch "System settings / Wacom Tablet" but : "No tablet detected". The tablet IS connected at boot time, triple checked, and if I deconnect-reconnect, nothing append.

---

### Post by mörgæs on 2016-07-05
Please run 

```
apt-cache policy xf86-input-wacom
```

once using the installed system and once using the live boot and post the results in CODE tags.

---

### Post by fossuvon on 2016-07-05
OK.

```

herve@grosse-machine:~$ apt-cache policy xf86-input-wacom
N: Impossible de trouver le paquet xf86-input-wacom


```

on boot USB
```

N: Unable to locate package xfc86-input-wacom

```

---

### Post by fossuvon on 2016-07-05
Sorry, a mistake, it was on boot usb
```

N: Unable to locate package xf86-input-wacom

```

---

### Post by mörgæs on 2016-07-05
Sorry, it should have been xserver-xorg-input-wacom.

---

### Post by fossuvon on 2016-07-06
I get :
```

herve@grosse-machine:~$ apt-cache policy xserver-xorg-input-wacom
xserver-xorg-input-wacom:
  Installé : 1:0.31.0-4
  Candidat : 1:0.31.0-4
 Table de version :
 *** 1:0.31.0-4 0
        500 http://ppa.launchpad.net/doctormo/wacom-plus/ubuntu/ trusty/main 
i386 Packages
        100 /var/lib/dpkg/status
     1:0.23.0-0ubuntu2 0
        500 http://fr.archive.ubuntu.com/ubuntu/ trusty/main i386 Packages

```
With USB boot :
```

ubuntu@ubuntu:~$ apt-cache policy xserver-xorg-input-wacom
xserver-xorg-input-wacom:
  Installed : 1:0.32.0@ubuntu3
  Candidate : 1:0.32.0@ubuntu3
 Version table :
 *** 1:0.32.0@ubuntu3 500
        500 http://archive.ubuntu.com/ubuntu xenial/main amd6
        100 /var/lib/dpkg/status

```

---

### Post by mörgæs on 2016-07-06
Strange. Your xserver-xorg-input-wacom in the live boot of 16.04 should be fine but still you don't get any connection. 

Regardless of this I suggest that you do a fresh install (not an upgrade) of 16.04. If we have to install and uninstall packages it's easier to work on a fixed operative system.

---

### Post by fossuvon on 2016-07-06
OK, thanks ; perhaps some old usb connectors ? My computer is 6 or 7 years old.

---

### Post by mörgæs on 2016-07-07
Almost all problems discussed in Ubuntuforum are software problems simply because software causes far more problems than hardware.

Your hardware is fine, else you would not get the correct ID 056a:033c. 

I still recommend that you do a fresh install of 16.04. Post back when that is done.

---

### Post by fossuvon on 2016-07-09
YES IT'S WORK !

Planty thanks :-)

But one problem : My tablet is detected on desktop (the mouse move when I move pen) and in gimp BUT not detected by system settings / wacom tablet ???

---

### Post by mörgæs on 2016-07-09
There might be small glitches for very new hardware like yours. I don't know of a solution but let's see if anyone else has a suggestion.

If you consider your main problem solved please mark the thread so.

Please also encourage other users to install the latest release when the question is about hardware support.

---

