---
title: "ATI Radeon 2100 Grahics Problem"
date: 2010-01-13
forum: Hardware
---

### Post by stevepetmonkey on 2010-01-13
Hello,
I have installed Ubuntu 9.1 on a new machine with an Asus M2A74-AM SE Motherboard, this has an integrated ATI Radeon 2100 Graphics Processor and I am getting slightly flickering/wobbling screen :(
I am loving Ubuntu apart from this problem so any help on changing the driver would be good, a few more details:

Ubuntu 9.1 (All updates applied)
ATI Radeon 2100
Max shared memory 256MN
Supports RGB max resolution of 2048x1536 @85 Hz


Not sure what this commands means but when I enter them I get this:
reece@reece-desktop:~**$ glxinfo | grep vendor**
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project
reece@reece-desktop:~$ 

also:
reece@reece-desktop:~$ glxinfo | grep "direct rendering"
direct rendering: Yes
reece@reece-desktop:~$ 

Please help, I really don't want Windows on my PC.
Steve.

P.S. I am a totally new to Linux.

---

### Post by MelDJ on 2010-01-13
have you installed the drivers from hardware drivers? 
if you did, i suggest you remove them and get the drivers from the ati website

---

### Post by stevepetmonkey on 2010-01-14
> **MelDJ said:**
> have you installed the drivers from hardware drivers? 
if you did, i suggest you remove them and get the drivers from the ati website

The driver was installed with the OS.
I have looked on ATI website and cannot find a Linux driver.
???
How do I install from hardware drivers?

---

### Post by Yellow Pasque on 2010-01-14
Your card is no longer supported by proprietary ATI drivers.

---

### Post by stevepetmonkey on 2010-01-15
> **Temüjin said:**
> Your card is no longer supported by proprietary ATI drivers.

So how do I tweak the one on the system then? Can't seem to change the refresh rate, perhaps that would help?

---

### Post by Yellow Pasque on 2010-01-15
> **stevepetmonkey said:**
> So how do I tweak the one on the system then? Can't seem to change the refresh rate, perhaps that would help?
What?

---

### Post by stevepetmonkey on 2010-01-15
> **Temüjin said:**
> What?

How do I change the settings so the graphics card works better with Ubuntu?

---

