---
title: "Can't set display resolution beyond 800X600 on ubuntu 10.10"
date: 2010-12-19
forum: Hardware
---

### Post by manishm on 2010-12-19
I have ASUS A7V400-MX motherboard and below is my display crd details. My monitor is Samsung SyncMaster591s. After installing ubuntu 10.10.  My machines doesn't detect monitor. it says 'unknown monitor' Also can't set display resolution beyond 800X600.  Please advise how to fix my display. 
lshw -c video
WARNING: you should run this program as super-user.
PCI (sysfs)  
^C
manish-A7V400-MX:~$ sudo lshw -c video
[sudo] password for manish: 
  *-display UNCLAIMED     
       description: VGA ***patible controller
       product: KM400/KN400/P4M800 [S3 UniChrome]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-2.0 vga_controller bus_master cap_list
       configuration: latency=32 mingnt=2
       resources: memory:e4000000-e7ffffff memory:e8000000-e8ffffff memory:e9000000-e900ffff

---

### Post by mrnettles on 2010-12-20
I have exactly the same problem. Straining to read from a small display in the middle of my screen.

---

### Post by theasprint on 2010-12-20
Hi,

Er, from what you have provided, I still can't identify your video card.

Could you kindly tell me what is your Video Card model?
(Like Nvidia 310M or ATI Radeon 5450? or Intel HD XXXX)

---

### Post by cascade9 on 2010-12-21
The video is there, its- 

> **manishm said:**
> S3 UniChrome

Oh dear. Not fun. This might help- 

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

---

### Post by davidmohammed on 2010-12-21
I agree - not fun

maybe try to manually get the openchrome driver to recognise the screen resolution you want e.g.

If you run:
gksudo gedit /etc/X11/xorg.conf
and paste this text:


```
Section "Device"
 Identifier "Configured Video Device"
 Driver "openchrome"
EndSection
Section "Monitor"
 Identifier "Configured Monitor"
 Option "DPMS"
 HorizSync 28-80
 VertRefresh 43-60
EndSection
Section "Screen"
 Identifier "Default Screen"
 Monitor "Configured Monitor"
 Device "Configured Video Device"
 DefaultDepth 24
 SubSection "Display"
  Depth 24
  Modes "1024x768"
 EndSubSection
EndSection
Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
EndSection

```

Save the file, close gedit and reboot. If the new setting is bad you can boot to root recovery mode and rename the file.

---

### Post by manishm on 2010-12-24
it worked for me. thank u :)

---

### Post by theonhighgod on 2010-12-27
thanks this really helped me, 

my monitor has a resolution of 1280x1024 i was able to change this using the "monitors" options found in system under preferences, i then set it to default.

---

### Post by naradluffy on 2011-10-19
> **davidmohammed said:**
> 
```
Section "Device"
 Identifier "Configured Video Device"
 Driver "openchrome"
EndSection
Section "Monitor"
.
.
. 
 
Screen "Default Screen"
EndSection

```
Save the file, close gedit and reboot. If the new setting is bad you can boot to root recovery mode and rename the file.
It's work. Thank you so much! :popcorn:

---

