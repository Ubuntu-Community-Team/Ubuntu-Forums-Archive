---
title: "Two HW problems with Dell Precision T5400 and Ubuntu Jaunty"
date: 2009-06-17
forum: Hardware
---

### Post by tzury on 2009-06-17
Hi,

I just got this high end workstation [link]("http://www.dell.com/us/en/business/desktops/precn_t5400/pd.aspx?refid=precn_t5400&cs=04&s=bsd").
Surprisingly, I cannot play any sound file and the display driver does not support rotating.

$ sudo lspci -v 

**shows:**

09:02.0 Audio device: Creative Labs SB X-Fi
	Subsystem: Creative Labs Device 6002
	Flags: bus master, medium devsel, latency 64, IRQ 18
	Memory at f7bfc000 (32-bit, non-prefetchable) [size=16K]
	Memory at f7c00000 (64-bit, non-prefetchable) [size=2M]
	Memory at f0000000 (64-bit, non-prefetchable) [size=64M]
	I/O ports at cce0 [size=32]
	Capabilities: [40] Power Management version 2
	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Kernel driver in use: CTALSA
	Kernel modules: ctxfi


**UPDATE:**
I've managed to solve this by downloading an open-source driver from creative site
and following the README file
get it at [http://support.creative.com/downloads/download.aspx?nDownloadId=10792]("http://support.creative.com/downloads/download.aspx?nDownloadId=10792")

---

### Post by kwanu on 2010-06-19
Hi, I have a similar trouble...
 
I am trying to install Ubuntu 9.04 on DELL Precision T5400, but I cannnot install.
I was doing following....
 
1. Insert iso CD and then the window for installing is coming up
2. select language : English
3. click on "Install Ubuntu"
 
When I click on this, I can see some messages..
 
Traceback (most recent call last)
...blabla....
__main__XStartupError : X server exited with return code 1
0% : scanning disks ...
0% : Detecting file system...
... blabla...
I cannot this part, because of too quick.
 
But, there is one special message about Audio something.
 
So, if you guys know what is the problem, please let me that.
 
I want to intall Ubuntu on DELL Precision T5400.
 
Thanks,

---

### Post by kwanu on 2010-06-19
One more thing...
 
If I type "$ sudo lspci -v" 

**shows:**

09:02.0 Audio device: Creative Labs SB X-Fi
           Subsystem: Creative Labs Device 6002
          Flags: bus master, medium devsel, latency 64, IRQ 5
          Memory at f49fc000 (32-bit, non-prefetchable) [size=16K]
          Memory at f4a0000 (64-bit, non-prefetchable) [size=2M]
          Memory at f000000 (64-bit, non-prefetchable) [size=64M]
          I/O ports at bce0 [size=32]
          Capabilities: [40] Power Management version 2
          Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-

---

