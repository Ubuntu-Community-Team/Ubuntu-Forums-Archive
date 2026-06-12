---
title: "AGP Card and inbuild VGA Chip conflict"
date: 2007-11-29
forum: Hardware &amp; Laptops
---

### Post by ankitsagwekar on 2007-11-29
I use a Asrock p4i45gv Chipset motherboard. It has an inbuild VGA chip. But I use a NVIDIA 6200LE agp card as my graphics card ( selecting it the primary display card in BIOS setup). Problem is that while installing Linux a IRQ conflict arise and Kernel Panic occurs
i contact my mobo vendor and ask him how to disable onboard VGA card they say that you cannot disable the on-board VGA adapter. All you can do is select which is the primary.
now i want to try disable or remove intel module 
how can i do in it ?
i try to blacklist intel module but i don't know how to do that
i m using ubuntu 7.10 & my onboard display driver is intel 845

---

### Post by Peter09 on 2008-03-15
Hi,
I have just been talking to someone else about the same problem. This is a known issue and there are lots of hits on google for 

"ASRock P4i45GV ubuntu".

 I could not see any solutions posted - just problems.

PC

---

### Post by ankitsagwekar on 2008-03-18
I love linux, but I really dissapointed and frustrated with this matter. Before I buy and install the Nvidia video card, I use to test almost every linux distro released or updated.

The only way to solve this matter is in some distros,(as ubuntu SuSE & Mandriva) is: 
adding in the file /etc/modprobe.d/blacklist a sentence 
"blacklist intel-agp"(no slash), so this way the system will discard the internal agp.

Change a little bit your /etc/X11/xorg.conf to look like this on Section Device:
Section "Device"
Identifier "Card0"
Driver "nv"
BoardName "GeForce FX 5200"
BusID "PCI:3:0:0"

Screen 0
#Option "UseDisplayDevice" "dfp"
#Option "MonitorLayout" "crt,crt"
#BusID "PCI:1:0:0"
#Option "sw_cursor" # needed for some ati cards
#Option "hw_cursor"
#Option "NoAccel"
#Option "ShowCache"
#Option "ShadowFB"
#Option "UseFBDev"
#Option "Rotate"
Option "UseInternalAGPGART" "no"
Option "NvAGP" "1"
Yours may be diferent, but, only set the BusID if you know it, if no, please comment the line.

---

