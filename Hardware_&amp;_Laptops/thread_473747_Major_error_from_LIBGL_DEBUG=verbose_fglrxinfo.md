---
title: "Major error from LIBGL_DEBUG=verbose fglrxinfo"
date: 2007-06-14
forum: Hardware &amp; Laptops
---

### Post by Infinia on 2007-06-14
**To me I think this might be a major problem for me... A really bad one...**
[B]
I open up my terminal and type in:[/B]
 LIBGL_DEBUG=verbose fglrxinfo
**The message I receive is:**
 libGL: XF86DRIGetClientDriverName: 8.34.8 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.34.8 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:0:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:0:0
[b]Can't open configuration file /etc/ati/fglrxrc: No such file or directory.
Can't open configuration file /etc/drirc: No such file or directory.
Can't open configuration file /home/infinia/.drirc: No such file or directory.
Can't open configuration file /etc/ati/fglrxrc: No such file or directory.
Can't open configuration file /etc/drirc: No such file or directory.
Can't open configuration file /home/infinia/.drirc: No such file or directory.[/b]
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9550/X1050 Series
OpenGL version string: 2.0.6334 (8.34.8)




Now, everything seems to be find except for the  Can't open configuration file messages and I'm very worried about them, and I'm a new Ubuntu user so I don't have any idea on how to fix it... *This **IS** a problem so don't tell me it isnt and to not worry about it, just don't tell me any of that junk...*

_I WANT TO KNOW HOW TO FIX THIS, I'M PRETTY WORRIED RIGHT NOW..._

---

### Post by Kegir on 2007-11-07
libGL: XF86DRIGetClientDriverName: 8.37.6 fglrx (screen 0)
libGL: OpenDriver: trying /usr/lib/dri/fglrx_dri.so
libGL: XF86DRIGetClientDriverName: 8.37.6 fglrx (screen 0)
drmOpenByBusid: busid is PCI:1:5:0
drmOpenDevice: minor is 0
drmOpenDevice: node name is /dev/dri/card0
drmOpenDevice: open result is 4, (OK)
drmOpenByBusid: drmOpenMinor returns 4
drmOpenByBusid: drmGetBusid reports PCI:1:5:0
Can't open configuration file /etc/ati/fglrxrc: No such file or directory.
Can't open configuration file /etc/drirc: No such file or directory.
Can't open configuration file /home/pcu/.drirc: No such file or directory.
Can't open configuration file /etc/ati/fglrxrc: No such file or directory.
Can't open configuration file /etc/drirc: No such file or directory.
Can't open configuration file /home/pcu/.drirc: No such file or directory.
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon X1200 Series
OpenGL version string: 2.0.6473 (8.37.6)


I'm having a similar problem.  I have compiz running fine but I have no direct rendering and I can't play 3d games like nexuiz or open arena.  Anyone have a solution.

---

### Post by wlc3069 on 2007-11-11
having thesame problem with my radeon x1600, if anyone has any help to give please do!!!

---

### Post by patryk77 on 2007-11-20
Also getting this error...

There is a package called driconf which generates those files...

But I can't get it to work either on my X1600 Pro

---

### Post by Beefeater on 2007-12-16
Did you guys ever fix this?

---

### Post by Cruciatum on 2008-03-20
Bump.

Getting same issue.

---

### Post by Mwiti on 2008-03-22
Hi all! I'm new...

Same problem, with ATI 9600, fglrx shipped with Ubuntu 7.10.

3D is ok, and Compiz works fine, but after a while Xgl server sucks 99% of CPU until deactivation of "window decoration"... I think is due to the direct rendering devolved to CPU 

driconf generate only home/user/.drirc but not the others

Googled for many solutions but nothing at moment...

Any update?

---

### Post by BixMix on 2008-03-28
Same Problem.  I've searched and tweaked, but no answers yet.  I don't think that this is necessarily related, but I get PCI bridge errors during start up.  Other than the fact that I can't get certain games to work, all is fine.

---

### Post by white_eagle-mk on 2008-03-30
I know dat! :) The problem is in the fglrx drivers itselfs.. You need to use the atis official drivers from ati.amd.com and use [this]("http://ubuntuforums.org/showthread.php?t=589637") guide, but with replacing the numbers from the newer drivers ( be careful though, the numbers can be confusing -- they go from higher to lower ) and this guide worked fantastically for my ATi Xpress 200m graphics card, which has 64 MB of memory and is integrated on the board, and it still worked out quite nicely... One more warning, you can't have a video and the effects running the same time, you must turn off the effects to se a video...

I hope this works for you.. :lolflag:

---

