---
title: "Breezy (and Dapper) on Toshiba Tecra A5"
date: 2006-01-20
forum: Hardware &amp; Laptops
---

### Post by sorrender on 2006-01-20
Toshiba Tecra A5 specs:

Mobile Intel Pentium M with 2MB cache level 2
Chipset Mobile Intel 915PM
ATI Radeon X600SE hypermemory
ethernet LAN Marvel Yukon 88E8053 GIGA
BIOS Acpi 1.0b
TFT secreen 14" 1280x768 WXGA
ALps touchpad
CD-Rw 24x/DVD-RW 8x
PCMCIA II slot
Bluetooth
IRDA
SD/MMC reader
4 USB 2
60 GB HD
1 GB RAM 

After 5 days, I finally give up.

First, all the installation process requires an Internet connection. The problems are:

1) Wired ethernet: the drivers provided for the Marvel Yukon Gigabit ethernet are buggy, and I lost  connection every time (and cause conflicts in the other computers).

2) Wireless: the Intel Pro Wireless drivers provided are unusable. Constantly resetting the miniPCI card; also, the lack of WPA support makes more difficult to connect to more secure wireless networks

When finally get "connected" using ethernet, the installation goes on (1 and a half hour; my system is spanish and I need to download aditional resources) and everything seems to work well.

But then you are struck with the video driver: fatal error, no screen found. Following the directions of other Threads in the forum, and using the console, I finally installed the driver for my ATI x600 SE video card. I can't understand why, in case of an unkonw card, Ubuntu doesn't try to start in graphical mode using any compatible mode (VGA, VESA, etc). It is much more easy to configure things (specially for non experts like me) in a graphical environment.

Well, with ubuntu 5.10 finally working in my portable, but with almost a lack of connectivity (for example, to browse my windows network it spends 1 to 3 minutes for level; so, to arrive at a level 3 volume, I spend barelly 9 minutes only to see the share; browsing the volume or copyng a file is a nightmare). Also, browsing Internet is unusable.

The mousepad drivers are not working (very sensible and buggy, I needed to plug a USB mouse). In Dapper the drivers are even worst, but it's still a beta.

So, I decided to give a try at the latest Dapper prerelase (relase 3), but things are worse: no liveCD support (also no live CD support for 5.10), no video drivers (needs the same solution), absolutely lost of wired connectivity and buggy and unstable wireless connectivity.

Now I'm using Ubuntu 5.10 inside VMWare VMplayer for windows XP (sigh), and everything goes well (slow, but well).

I hope the final release of Ubuntu 6.04 Dapper will solve all my problems (at least half of them).

P.D.: Also tried Fedora Core 4 with no luck. The drivers problem is a plague in all linux distros. Oh my!

---

