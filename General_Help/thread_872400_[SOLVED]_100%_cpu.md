---
title: "[SOLVED] 100% cpu"
date: 2008-07-27
forum: General Help
---

### Post by DougieFresh4U on 2008-07-27
This is gonna be long nite!!
Just did a fresh Hardy install and all went well (Linskys USB adapter worked our of the box, great)
CPU is running at 100%. I have used this machine for the last 5 releases and never had this problem. It's an older Intel.I was away for a year, so I am not sure if there is anything I am not aware of about Hardy and the high CPU usage. Can any one please help me figure this out? Thanks

---

### Post by tamoneya on 2008-07-27
can you give us the output of "top" in terminal(applications -> accessories -> terminal).  It constantly updates itself but we just need one "frame" of it.

---

### Post by DougieFresh4U on 2008-07-27
Here it is also screen is 'jumpy'

---

### Post by tamoneya on 2008-07-27
that tells me that you are averaging about 30% CPU load.  What is telling you that you have 100% CPU load.  Is it acting sluggish?

---

### Post by DougieFresh4U on 2008-07-28
I go into 'System Monitor' Yes it is dragging or sluggish as you asked Also, why is the screen so jumpy when I'm going through a page, scrolling? I have it set for smooth scrolling,  when I stop moving scroll wheel, page keeps going for a few seconds. Is there a bug I am not aware of? Thanks for your help

---

### Post by tamoneya on 2008-07-28
the CPU usage measurement of gnome-system-monitor is not very accurate because its measurement techniques causes the CPU to do a bunch of extra work.  the top command is much more accurate.

---

### Post by DougieFresh4U on 2008-07-28
thanks for your helping me understand the CPU. Any idea whats causing the buggy actions?

---

### Post by tamoneya on 2008-07-28
the sluggish scrolling may just be the improper graphics card drivers.  Causing it to update to slowly.  Do you have any specs on your graphics card.

```
lspci
```

---

### Post by tinny on 2008-07-28
> **DougieFresh4U said:**
> thanks for your helping me understand the CPU. Any idea whats causing the buggy actions?

Looks like X is working hard (your windowing system).

What type of graphics card do you have? ATI?

Gutsy picked up my ATI video card but Hardy did not. My graphics performance was rubbish. I set "fglrx" as my driver. Do you have "fglrx" as your configured video driver in /etc/X11/xorg.conf 

Setup
In hardy something like...
```

sudo dpkg-reconfigure -phigh linux-restricted-modules-`uname -r`
sudo insmod /lib/modules/`uname -r`/volatile/fglrx.ko

```


Then restart...

Of course most of this post is useless if you don't have an ATI card, but it may help someone else.

---

### Post by DougieFresh4U on 2008-07-28
dougie@DougiesLeanMachine:~$ lspci
00:00.0 Host bridge: Intel Corporation 82810E DC-133 (GMCH) Graphics Memory Controller Hub (rev 03)
00:01.0 VGA compatible controller: Intel Corporation 82810E DC-133 (CGC) Chipset Graphics Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 05)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 05)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 05)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 05)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 05)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 05)
01:00.0 Modem: ALi Corporation SmartLink SmartPCI561 56K Modem
01:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 03)
dougie@DougiesLeanMachine:~$

---

### Post by tinny on 2008-07-28
I think you need the xserver-xorg-video-intel package.

Can you post your /etc/X11/xorg.conf ????

You should be using the i810 driver. (Driver "i810" under the "Device" section of xorg.conf)

---

