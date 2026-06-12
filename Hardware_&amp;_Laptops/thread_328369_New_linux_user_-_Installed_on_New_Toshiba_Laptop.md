---
title: "New linux user - Installed on New Toshiba Laptop"
date: 2006-12-30
forum: Hardware &amp; Laptops
---

### Post by Unreallinux on 2006-12-30
I recently bought this laptop:
[http://www.circuitcity.com/ssm/Toshiba-Satellite-15-4-Widescreen-Notebook-PC-L35-S2161/sem/rpsm/oid/165319/catOid/-12963/rpem/ccd/productDetail.do](http://www.circuitcity.com/ssm/Toshiba-Satellite-15-4-Widescreen-Notebook-PC-L35-S2161/sem/rpsm/oid/165319/catOid/-12963/rpem/ccd/productDetail.do)

I love it, I got it for $400 with a printer/scanner, and Zone Alarm Secuity suite for free.
Well I decided that I would maybe give linux a try since I have some time to reformat if anything goes wrong. :P

Anyway I had ordered a ubuntu lts disk and I used it on my laptop. I gave it a 20 gig partition and 1gig swap and everything seems to go fine.

But I have a few issues. I can't get wireless to work and the fans on my laptop don't seem to be running..(thats all I can tell so far. The laptop has onboard ati graphics and I'm not sure how to test if everything is working.)

Can anyone tell me of some ways to get wifi to work, fix my fans, and a easy way to see if all my hardware is working? Thanks. (please keep it simple as I have absolutely no linux knowledge.)

---

### Post by Metaljaz on 2006-12-30
to get information on your particular laptop take a look at the below link. If its no help post back.

[http://www.linux-laptop.net/](http://www.linux-laptop.net/)

---

### Post by doviende on 2006-12-31
Also, with Toshiba Satellite laptops, you should be aware that if it has a Phoenix BIOS, then it won't use the normal toshiba laptop tools from the "toshutils" package.  I have a Satellite A100 and it has a Phoenix BIOS, so i'm trying to get some of the extra things to work using the omnibook drivers from omnibook.sourceforge.net

I can't see your Satellite L35 model on that linux-laptops link, so i'll assume you'll come looking back here for help.  What you should do is post the output from the lspci command so that we know what kind of hardware you have.  Once we know what type of Wifi card you have, we'll be able to direct you to the right place.  Also, when you reboot, take a look to see if it says "Phoenix BIOS" at the very first screen, or if it says Toshiba BIOS.

---

### Post by Unreallinux on 2007-01-01
Ok thanks for the help.

My laptop does have the pheonix bios. 
I have noticed that the fans and wifi card are working but I can't use wifi unless I choose to unsecure my router.(so ubuntu can't use WPA?)

I also noticed that my headphone jack isn't working. Any and all help is much appreciated!

I would post that list from the command you asked but I don't know what you mean...(I have literally never used linux before now).

On the plus side I did get automatix and now I can do most stuff that I did on windows!

---

### Post by Unreallinux on 2007-01-01
Well I'm not as big a noob as I though. :D
Here is the log from lspci:

0000:00:00.0 Host bridge: ATI Technologies Inc: Unknown device 5a31 (rev 01)
0000:00:01.0 PCI bridge: ATI Technologies Inc: Unknown device 5a3f
0000:00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
0000:00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
0000:00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller  (rev 80)
0000:00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
0000:00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE C ontroller ATI (rev 80)
0000:00:14.2 0403: ATI Technologies Inc: Unknown device 437b (rev 01)
0000:00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
0000:00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
0000:01:05.0 VGA compatible controller: ATI Technologies Inc: Unknown device 5a6 2
0000:09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 0 1)
0000:09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C /8139C+ (rev 10)
0000:09:04.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 0 01a (rev 01)

---

### Post by Metaljaz on 2007-01-01
0000:09:04.0 Ethernet controller: Atheros Communications, Inc.: Unknown device 0 01a (rev 01)

Ok..You did not say what your card was but it looks like it has an Atheros based
chipset. A lot of cards with that chipset usually work out of the box.

tell us about your card.

---

### Post by Unreallinux on 2007-01-01
It actually is working but I can't connect to my network because it seems ubuntu can't use WPA-PSK(well thats what my router calls it anyway. :P).
Also what about the ati integrated card and sound cards. Are they supposed to work as well? My headphone and mike jacks aren't working.(I'm not sure about the ati card)

---

### Post by Metaljaz on 2007-01-01
try this site:

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)

---

### Post by Metaljaz on 2007-01-01
or this thread:

[http://www.ubuntuforums.org/showthread.php?t=263136](http://www.ubuntuforums.org/showthread.php?t=263136)

---

### Post by castoroil97 on 2007-03-08
I have an L35.  Install for 6.10 edgy went great.  My fan runs and so does the wireless.  I will try to pay attention to the bios info on the next boot.  My wireless is atheros, sorry dunno the chipset at this time.
I am having the same problem with my headphone jack and I have not tried the microphone.  If I find anything I will let u know, but I would like to get it working of course.

my lspci

00:00.0 Host bridge: ATI Technologies Inc Unknown device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:12.0 IDE interface: ATI Technologies Inc ATI 4379 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI (rev 80)
00:14.2 Audio device: ATI Technologies Inc Unknown device 437b (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
09:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
09:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
09:04.0 Ethernet controller: Atheros Communications, Inc. AR5005G 802.11abg NIC (rev 01)

---

### Post by jml on 2007-03-08
Ubuntu's default network manager does not support WPA encryption.  You will need to download and install two applications, network-manager and network-manager-gnome.  This app supports WPA-PSK encryption.  Once installed it will place an icon in the upper right hand corner of your screen. Its functions are accessed by either left or right clicking on the icon.  Hope this helps.

Joe

---

### Post by airencracken on 2007-03-14
The above WPA stuff should work I did much the same and WPA now works on my laptop. (Toshiba l35-s2171). However, I too am having the Headphone/Microphone issue and I haven't found any information regarding it.

---

