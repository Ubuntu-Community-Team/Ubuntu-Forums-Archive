---
title: "WPC54G ver 3"
date: 2007-01-21
forum: Hardware &amp; Laptops
---

### Post by glytle on 2007-01-21
Greetings,

After following 2 different tutorials each, on installing ndiswrapper, insatlling LINKSYS WPC54G V 3, and reloading Ubuntu 6.06 LTS 3 times,  have reinstalled Windows 2000, in which I installed the card in a few minutes. I am a profficient computer user, ( assistant network admin) . Many times have I tried to install NDISWRAPPER, Does anyone have a more definite strategy on installing this hardware? I tried the chipset drivers for various chipsets, various cards etc. I am willing to give this another try, but need assistance or something. 
My laptop:
NEC Versa SXi
700 Mhz PIII
512 ram
CD/RW
Linksys WPC54G ver. 3

Any help others could offer wouldbe greatly appreciated, I loved the look and function of Ubuntu, but I have to have wireless on my portable.
Thanks,
Greg

---

### Post by yonux on 2007-01-27
download wpc54g driver (ver.1, 2, 4)
if ver3, copy from cd

(bcmwl5.sys  LSBCMNDS.inf)

# apt-get install ndiswrapper-utils bcm43xx-fwcutter
# bcm43xx-fwcutter bcmwl5.sys
# cp *.fw /lib/firmware
# ndiswrapper -i LSBCMNDS.inf

edit property from network-admin
select active

i'm sorry. but i don't know english

good luck

---

### Post by yonux on 2007-01-27
download wpc54g driver (ver.1, 2, 4)
if ver3, copy from cd

(bcmwl5.sys  LSBCMNDS.inf)

# apt-get install ndiswrapper-utils bcm43xx-fwcutter
# bcm43xx-fwcutter bcmwl5.sys
# cp *.fw /lib/firmware
# ndiswrapper -i LSBCMNDS.inf

edit property from network-admin
select active

i'm sorry. but i don't know english

good luck

---

### Post by jasonbain on 2008-06-28
I have the WPC54G v3.1 card working on my IBM Thinkpad T21.

hardware using the list pci utility:

$lspci 
Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

First, I installed Windows Wireless Drivers graphical front end for ndiswrapper (installation of Windows WiFi drivers) through the Hardy Add/Remove programs.  

Second, I browsed the CD for the .inf file in the drivers directory for win98.   I had no luck with the 2k/xp drivers.   

the drivers installed and I was up in running in less than an hour.  I had to struggle with the win2k drivers for a good half hour before I tried the win98 driver.  It works great and I have had no problems.

cheers and good luck,
jason

---

