---
title: "Fujitsu-Siemens Amilo M7440 X11 Problem"
date: 2005-08-29
forum: Hardware &amp; Laptops
---

### Post by LeoKhan on 2005-08-29
Hi,
 
 I succesfull installed Kubuntu on my Amilo M7440 laptop. But X11 doesn't work properly. Altough I can see boot screen I cannot see anything on login. There is only black screen. Interestingly when I boot my laptop with an external monitor connected, external monitor screen and laptop's LCD works. Then I disconnect external monitor LCD continue working until I reboot.
 My highest resolution is 1024-768 and adapther is intel i915GM...
 
 Can anyone help me?

---

### Post by Neffscape on 2005-09-07
I have the same problem with an "old" Amilo A 1400+.
When I was running warty I had no problems with Xfree86. Unfortunately skipping from Xfree86 to Xorg I encoutered the same problem you are describing.

For the moment I'm running ubuntu hoary but I'm still using the old xfree86 x server, but now I would like to resolve those problems... I cannot even compile a tarball because new programs require xorg librairies....


Any tip?


My Laptop data:

# Screen: 15' lcd TFT XGA 1024x768x32 @ 60Hz
# CPU: AMD Athlon XP Mobile 1400+ (256Kb L2 Cache)
# Board: 266MHz FSB ; Bios Phoenix NoteBIOS 4.0 Rel. 6.1
# Mem: 256 Mb DDR (shared with GPU)
# GPU: ATI RADEON IGP 320M = TVout 5/128Mb , CRT=2048x1536x32 cpu=ATI U1 (C6), dac@350Mhz
# Disks: hdd IDE toshiba 20Gb + DVD/CD/CDRW + fdd3.5
# Audio: AC97 16bit stereo + 2 frontal speakers + embed mini mic
# Modem: onBoard V90 56K + RJ11 plug
# Lan : 10/100 Mbps , + RJ45 plug
# Mouse : Alps Electric Pointing device
# Keyboard : French Mapping (azerty) , soft & silent w/ 2 extra keys (web+mail)
# I/O : 2 pcmcia ,3 usb , ps/2 , ieee 1394 (firewire) , 1 serial (com) , 1 parallel (lpt/epp)
# Design : Metal Gray/Blue for 3 Kg
# Power Supply : Sector ASTEC SA80-3105 : 100/240V or Battery (3hours Max / 500 cycles)



Thanks a lot!

---

### Post by ubuntunewbieit on 2005-09-15
same problem with an amilo xp-mobile 2400+
no problem with xfree....but with xorg black screen on login and nothing to do....hoary or breeze no dofference.

---

### Post by krale on 2005-09-16
[QUOTE=ubuntunewbieit]same problem with an amilo xp-mobile 2400+
no problem with xfree....but with xorg black screen on login and nothing to do....hoary or breeze no dofference.[/QUOTE]

I have exactly the same problem, I wonder if there is no support for the TI RADEON IGP 320M chipset in Xorg???

Can this problem be solved?

---

### Post by ubuntunewbieit on 2005-09-16
well i tried also to connect an external monitor as leokan ....but no way to get ubuntu with xorg work.....i tried also gnoppix (based on ubuntu) but same....i hope someone can help us :(

---

### Post by Neffscape on 2005-09-17
I found a solution!

to make your computers works with the latest Xorg server you have to reconfigure it after the installation.
When your screen become black restart your computer, enter in the GRUB menu by pressing ESC and select "Recovery Mode".
The system will boot without X support. When everything is charged type in the terminal:

$ sudo dpkg-reconfigure xserver-xorg

During the reconfiguration of your Xserver pay particulary attention in the section when the configuration program ask you about your videocard memory. Type carefully the amount of your card memory in Kilobytes (If you know the amount in MB you can use this converter to know the size in KB: [http://www.egret.net/kb__mb.htm)](http://www.egret.net/kb__mb.htm)).

When the configuration program ends, type in the shell ctrl+D. If the data you inserted are good your Xorg server will start properly.

Good luck!

---

### Post by ubuntunewbieit on 2005-09-18
i just tried it several times (at least 2 every new xorg release one with frame buffer kernel on one off) no way on amilo with xp2400+ and ati igp320m

any other suggestion?;)

---

