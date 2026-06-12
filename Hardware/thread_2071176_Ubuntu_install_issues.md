---
title: "Ubuntu install issues"
date: 2012-10-14
forum: Hardware
---

### Post by profnova on 2012-10-14
So after several hours i am still unable to install Linux with either the disc or wubi both have different issues i will start with the disc version.
so i start the installation everything is fine then i click something different as i want to install it to a different hard drive that where the first issue start only a few of my hard drives the only drives found are my external which i don't want to install to my ssd which is for windows and my 1Tb raid the other which arnt detected are either on raid redy sata in ide mode and on a different controller on achi mode i tried swapping them around no joy even with only 1 drive installed so gave up with them then tried to install it to my 1tb raid doesn't work i get a fatal error and cant install the boot loader anywhere then i try installing on the ssd in a partition same issue apart from i doesn't tell me any error there just isn't a boot loader for Linux anywhere. so gave up with the disc and went to try wubi. first try installing on the ssd when it goes to complete the installation it says no root file system is defined so i try formatting the partition as ext2 and i just wont boot to the partition then i try installing it on another drive and same issue with disc no boot loader. so now i am fresh out of ideas and i rely want to use linux as it looks like a good os and i don't want to run it through virtual means as it just to slow.

srry for the massive wall of text but the more info i give the better. ;)
my pc specs are
amd fx-8150 3.6ghz oc to 4.1
Crosshair V Formula motherboard
asus ati radeon hd 7970 main gpu
saphire ati radeon 5770 secondary gpu runs my second screen and not in crossfire
HDD's
Samsung 830 128gb ssd Linux detect this drive fine
2 segate baracuda 7.2k rpm in raid 0 linux detect this drive fine
segate pipeline hd 5.8k rpm :p 500gb linux does not detect this drive
western digital caviar green 5.4k rpm 2tb linux does not detect this drive
Hitachi GST Deskstar 7.2k rpm 80gb linux does not detect this drive

---

### Post by inferno92 on 2012-10-14
unfortunately some people (such as me) have computers that act "special". I've also had trouble getting it to work with wubi and disk. I tried the use drive rout and it worked as long as i set the boot order to usb 1st then i was able to installed it:). You should prob try the usb and set boot order so usb/floppy it 1st. Just make sure your windows is backed up(i broke mine >.>)

---

