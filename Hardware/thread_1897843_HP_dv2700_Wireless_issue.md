---
title: "HP dv2700 Wireless issue"
date: 2011-12-20
forum: Hardware
---

### Post by Neo Phoenix on 2011-12-20
I had this laptop for quite sometime, im a big fan of ubuntu but never got around to installing it on this machine.

So this past weekend i had some free time and the OS in the laptop was starting to annoy the hell out of me. So i figured i'd give this a shot.

I downloaded ubuntu 11.10 and installed it as the sole OS for the laptop.

I booted it up and everything looked fantastic! i love the sidebar and the interface as a whole was stunning. 

So i figured i would check my email and get some programs for the system, and there lied the issue. I couldn't connect to my wireless router.

i already configured everything yet it says "firmware disabled"

but the switch for wifi on the HP dv2700 laptop is turned on but the light(the small led indicator) is red which indicates its off.

So this is where i am stuck, i see that this is a common issue and but sadly i dont see any solutions :(

would i have to go back to the OS that should not be named? 

and i am not that linux savvy so if the solution is step by step i'd appreciate it :)


Thanks in Advance!

---

### Post by N00b-un-2 on 2011-12-20
post the output of lspci -nn.  If I know what wireless card you have I can start helping troubleshoot.  Also, check your settings ins BIOS and make sure its not disabled there.  If there is another OS on the laptop, boot into it and make sure Wifi isn't turned off and then reboot into Linux.  I've ran into all kinds of goofy problems with hardware deciding not to work because of flags set in other OSes on HP DV2X and DV3X series laptops.
That being said, the most likely reason its not working is your wireless card is likely blacklisted and just needs to be reenabled.

---

### Post by Neo Phoenix on 2011-12-20
Thanks for the reply!

1. No idea how to do lspci -nn thing, like i said i am an absolute noob when it comes to linux. I use it for its ease and the fact that its virus free :D

2. Will do, cant believe i forgot about checking BIOS. Doh!

3. Dont have another OS on board, i installed this after a complete and thorough format so Ubuntu 11.10 is the sole OS.


Thanks for the help again! Apperciate it!

---

### Post by N00b-un-2 on 2011-12-20
Good choice to switch to Linux.  Welcome to the wonderful world of learning to fix it yourself!

to enter that command, open a terminal window.  Assuming you're using Ubuntu with Unity, just type Terminal into the search field and it will find it.  Or hit alf+f2 and type gnome-terminal and hit enter.
then type lspci -nn in the terminal and post back the output of the command here.

---

### Post by Neo Phoenix on 2011-12-20
sweet!

i am not home right now but i will post back the output as soon as i get home.

Thanks again!

---

### Post by Neo Phoenix on 2011-12-20
so i did the lspci thing and here is the output(sorry about the huge post) :P

00:00.0 Host bridge [0600]: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub [8086:2a00] (rev 0c) 
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 0c) 
00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 0c) 
00:1a.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 [8086:2834] (rev 03) 
00:1a.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 [8086:2835] (rev 03) 
00:1a.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 [8086:283a] (rev 03) 
00:1b.0 Audio device [0403]: Intel Corporation 82801H (ICH8 Family) HD Audio Controller [8086:284b] (rev 03) 
00:1c.0 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 [8086:283f] (rev 03) 
00:1c.1 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 [8086:2841] (rev 03) 
00:1c.2 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 [8086:2843] (rev 03) 
00:1c.3 PCI bridge [0604]: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 [8086:2845] (rev 03) 
00:1d.0 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 [8086:2830] (rev 03) 
00:1d.1 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 [8086:2831] (rev 03) 
00:1d.2 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 [8086:2832] (rev 03) 
00:1d.7 USB Controller [0c03]: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 [8086:2836] (rev 03) 
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev f3) 
00:1f.0 ISA bridge [0601]: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller [8086:2815] (rev 03) 
00:1f.1 IDE interface [0101]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller [8086:2850] (rev 03) 
00:1f.2 SATA controller [0106]: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller [8086:2829] (rev 03) 
00:1f.3 SMBus [0c05]: Intel Corporation 82801H (ICH8 Family) SMBus Controller [8086:283e] (rev 03) 
05:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller [11ab:4353] (rev 14) 
07:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01) 
08:09.0 FireWire (IEEE 1394) [0c00]: Ricoh Co Ltd R5C832 IEEE 1394 Controller [1180:0832] (rev 05) 
08:09.1 SD Host controller [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter [1180:0822] (rev 22) 
08:09.2 System peripheral [0880]: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter [1180:0592] (rev 12) 
08:09.3 System peripheral [0880]: Ricoh Co Ltd xD-Picture Card Controller [1180:0852] (rev 12)

---

### Post by N00b-un-2 on 2011-12-21
Okay, you have a Broadcom BCM4312 wireless card, which just so happens to be the same exact one I have in my old HP DV2941SE :D  To get your Wifi card working you just need to install the drivers, which will require an internet connection, so it's a catch 22.  I've run into this issue OVER AND OVER AND OVER fixing computers.  My recommendation is to get yourself a Netgear WG111 V2/V3 USB dongle.  They are cheap, readily available and supported on virtually every operating system -- Windows 98/2000/XP/Vista/7, all Linux distros after kernel 2.24, FreeBSD and OSX 10.4 and up.  You could also do what I do when I'm making house calls and someone can't remember or doesn't know the WPA key to their wifi network (happens more often than you would think).  I bring my (rooted) Android phone with me and tether to it in the absence of the ability to connect wirelessly.  Of course, I keep the drivers on my phones SD card.  But anyway, after you get yourself connected to the internet by some means.

hit alt+f2 and enter the command

```
gksu jockey-gtk
```

Then it will ask you for password.  Install any proprietary drivers you need.  You will probably need the BCM43XX driver and the STA driver.

Reboot your computer and enjoy using your wifi

---

### Post by Neo Phoenix on 2011-12-21
> **N00b-un-2 said:**
> Okay, you have a Broadcom BCM4312 wireless card, which just so happens to be the same exact one I have in my old HP DV2941SE :D  To get your Wifi card working you just need to install the drivers, which will require an internet connection, so it's a catch 22.  I've run into this issue OVER AND OVER AND OVER fixing computers.  My recommendation is to get yourself a Netgear WG111 V2/V3 USB dongle.  They are cheap, readily available and supported on virtually every operating system -- Windows 98/2000/XP/Vista/7, all Linux distros after kernel 2.24, FreeBSD and OSX 10.4 and up.  You could also do what I do when I'm making house calls and someone can't remember or doesn't know the WPA key to their wifi network (happens more often than you would think).  I bring my (rooted) Android phone with me and tether to it in the absence of the ability to connect wirelessly.  Of course, I keep the drivers on my phones SD card.  But anyway, after you get yourself connected to the internet by some means.

hit alt+f2 and enter the command

```
gksu jockey-gtk
```

Then it will ask you for password.  Install any proprietary drivers you need.  You will probably need the BCM43XX driver and the STA driver.

Reboot your computer and enjoy using your wifi

awesome! thanks a load!

Is there somewhere i could perhaps download the driver to a usb drive and then install it with ubuntu, i know you can do this with windows(i do it quite a lot) but i am not so sure about linux.

Atleast i see a light at the end of the tunnel now! thanks again, appreciate it!

EDIT: Seems like you can Yay! :D

---

### Post by N00b-un-2 on 2011-12-21
sort of.  There are lots of ways that you can grab the deb packages, I suppose the easiest way would be to open up nautilus as root (alt+f2 gksu nautilus) and browse to /var/cache/apt/archives.  Any deb packages you have recently installed using apt will be located in there.

---

### Post by Neo Phoenix on 2011-12-21
> **N00b-un-2 said:**
> sort of.  There are lots of ways that you can grab the deb packages, I suppose the easiest way would be to open up nautilus as root (alt+f2 gksu nautilus) and browse to /var/cache/apt/archives.  Any deb packages you have recently installed using apt will be located in there.

There is a new issue now. Ubuntu 11.10 has issues installing .deb files.

i tried a LOT of solutions, but in the end i just got fed up and switch to 10.04

Hopefully the next release will be a bit more "broadcom friendly" although i doubt it :P It's not like the guys at ubuntu dont have better things to do!

---

### Post by N00b-un-2 on 2011-12-22
to manually install a .deb package you should use the terminal.  A lot of people will tell you to use the software manager, but I've had much better success with dpkg

open the terminal
```
alt_f2 gnome-terminal
```

move to the directory your .deb package is in, eg:
```
cd /home/your user name/Downloads/
```

install the deb package
```
sudo dpkg -i *.deb
```

assuming that the deb you downloaded is in fact the correct architecture for your computer and does not conflict with other packages, has satisfied all dependencies the package will install.  If anything goes wrong the terminal will tell you.

---

### Post by Neo Phoenix on 2012-01-01
> **N00b-un-2 said:**
> to manually install a .deb package you should use the terminal.  A lot of people will tell you to use the software manager, but I've had much better success with dpkg

open the terminal
```
alt_f2 gnome-terminal
```

move to the directory your .deb package is in, eg:
```
cd /home/your user name/Downloads/
```

install the deb package
```
sudo dpkg -i *.deb
```

assuming that the deb you downloaded is in fact the correct architecture for your computer and does not conflict with other packages, has satisfied all dependencies the package will install.  If anything goes wrong the terminal will tell you.

Thank you so much! 
It worked and i was able to install all the deb packages like that and get the wifi activated! Thanks again!

---

### Post by N00b-un-2 on 2012-01-01
I'm glad it worked for you

---

