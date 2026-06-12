---
title: "Ubuntu 9.04 won't  install or live boot on XFX Geforce 8200 MOBO"
date: 2009-08-11
forum: Installation &amp; Upgrades
---

### Post by chewbakker82 on 2009-08-11
Hi everybody,
 
I'm trying to get Ubuntu 9.04 to live boot or install on my self built pc. I can make it to the Ubuntu main screen, but when choosing "Run Ubuntu without changes to computer" or "Install", all I get is a white cursor in the corner of screen and I can hear the cd stop spinning. I tried F6 and chose ACPI=off. I then got the error message "Try booting with PNPBios=off" (I forget the exact wording, but I'm sure you guys know it.)Tried that option from F6, same resluts. When accessing my Bios the PNPBIOS option is already set to off. I tried with the setting on and got the same message. I read updating the BIOS can solve this, I flashed with latest update from manufacturer but issue remains. This also happens when I tried Kubuntu and Fedora, so I think my motherboard just has a problem with Linux. My motherboard is an XFX Geforce 8200. Here are my specs.
 
XFX Geforce 8200 MCP Socket AM2+
AMD Athlon X2 64 4600+ 2.46Ghz
4 GB Corsair RAM 800MHz DDR2
500GB Western Digital SATA HD
SATA DVD RW Drive
Nvidia Geforce 9500 PCI-e video card
500 watt power supply
 
 
The pc will boot Windows XP and Windows 7 without issue. I've been messing with this now for months, I really want to use Ubuntu on my main pc I think it's awesome. I have it installed on my older laptop but I want it on my more powerful pc. I've been studying Linux terminal and I really want to set up a secure, stable system. I'm worried that there is no way my mobo will boot it, but I hope that is not the case. Anyone's help on this would be greatly appreciated.

---

### Post by Moop on 2009-08-11
Try the alternate installer cd. It's a text based install but you'll end up with the same Ubuntu.

---

### Post by ZachMitchell on 2009-09-02
I also have a GeForce 8200 motherboard. The new linux kernel that ships with Ubuntu 9.04 doesn't like the 8200 for some reason. What I've done before is installed 8.10, then upgraded to 9.04 but selected to use the previous kernel in GRUB and eventually removed the new kernel from the GRUB menu. I'm anxious to see if 9.10 works any better on my system. Right now I'm just using 8.10 because I don't really have the time nor patience to tweak and play around with trying to get 9.04 to work.

---

### Post by chewbakker82 on 2009-09-21
Yeah this motherboard won't work even under those conditions. So guess what? I bought a new motherboard haha. I got an Asus motherboard with a geforce 7025 card built in and 64 bit 9.04 runs perfect, even with high graphics settings. I put the 8200 into a different case and built it as a windows pc for somebody. If you can't fix it, open your wallet.

---

