---
title: "where to change wrongly detected hardware"
date: 2005-04-18
forum: Hardware &amp; Laptops
---

### Post by mephisto56 on 2005-04-18
I installed ubuntu but it didn't correctly detected my wifi card and took another one. I can't find where to change it to the correct one (a linksys wrt54g, which I've read is supported in ubuntu). 
Probably a newbie question so I hope someone will help me. :) Thanks.

---

### Post by nad on 2005-04-18
An interesting feature of linux is that it will usually not install a driver module if it does not find hardware support for it. What driver is loaded? From a terminal screen, what is the output of the commands ' iwconfig ' and ' lspci ' and ' lsmod | grep -i ipw ' ?

Dan M

---

### Post by mephisto56 on 2005-04-19
It won't let me save to my floppy. :( But it reports it as some texas instruments card.

---

### Post by heimo on 2005-04-19
Did the card still work? Lots of driver development is based on chips, because one chip can be in range of products with different marketing names. It's possible that the kernel module (which implements the support for device) is actually correct, but only wrong name is shown.
 
You should try to configure this one to work, and if it seems impossible, only then consider that it's actually wrong module. (I try to do some fact checking to back my comments.)
 
EDIT: I'm confused. Is it Linksys WPC11 card? Then it could have Realtek chipset. You could give more information by running those commands nad suggested.

---

### Post by mephisto56 on 2005-04-19
Ok, I've managed to save it to floppy with the help of knoppix.  :roll: 

mephisto56@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g/b+  ESSID:"STA14BEEC"  Nickname:"acx100 v0.2.0pre8"
          Mode:Auto  Channel:1  Access Point: 00:00:00:00:00:00
          Bit Rate:1 Mb/s   Tx-Power:15 dBm   Sensitivity=1/3
          Retry min limit:7   RTS thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth1      no wireless extensions.

sit0      no wireless extensions.

mephisto56@ubuntu:~$ lspci
0000:00:00.0 Host bridge: nVidia Corporation nForce2 AGP (different version?) (r ev a2)
0000:00:00.1 RAM memory: nVidia Corporation nForce2 Memory Controller 1 (rev a2)
0000:00:00.2 RAM memory: nVidia Corporation nForce2 Memory Controller 4 (rev a2)
0000:00:00.3 RAM memory: nVidia Corporation nForce2 Memory Controller 3 (rev a2)
0000:00:00.4 RAM memory: nVidia Corporation nForce2 Memory Controller 2 (rev a2)
0000:00:00.5 RAM memory: nVidia Corporation nForce2 Memory Controller 5 (rev a2)
0000:00:01.0 ISA bridge: nVidia Corporation nForce2 ISA Bridge (rev a3)
0000:00:01.1 SMBus: nVidia Corporation nForce2 SMBus (MCP) (rev a2)
0000:00:02.0 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:02.1 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:02.2 USB Controller: nVidia Corporation nForce2 USB Controller (rev a3)
0000:00:04.0 Ethernet controller: nVidia Corporation nForce2 Ethernet Controller  (rev a1)
0000:00:05.0 Multimedia audio controller: nVidia Corporation nForce MultiMedia a udio [Via VT82C686B] (rev a2)
0000:00:06.0 Multimedia audio controller: nVidia Corporation nForce2 AC97 Audio Controler (MCP) (rev a1)
0000:00:08.0 PCI bridge: nVidia Corporation nForce2 External PCI Bridge (rev a3)
0000:00:09.0 IDE interface: nVidia Corporation nForce2 IDE (rev a2)
0000:00:0c.0 PCI bridge: nVidia Corporation nForce2 PCI Bridge (rev a3)
0000:00:0d.0 FireWire (IEEE 1394): nVidia Corporation nForce2 FireWire (IEEE 139 4) Controller (rev a3)
0000:00:1e.0 PCI bridge: nVidia Corporation nForce2 AGP (rev a2)
0000:01:07.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Inter face
0000:01:0b.0 RAID bus controller: Silicon Image, Inc. (formerly CMD Technology I nc) SiI 3112 [SATALink/SATARaid] Serial ATA Controller (rev 02)
0000:02:01.0 Ethernet controller: 3Com Corporation 3C920B-EMB Integrated Fast Et hernet Controller [Tornado] (rev 40)
0000:03:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 ND [Rad eon 9700 Pro]
0000:03:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9700 P ro] (Secondary)
mephisto56@ubuntu:~$ lsmod|grep -i ipw
mephisto56@ubuntu:~$


You could be right that it is a texas instruments chipset. I've found nothing about it in the manuals on the cd-rom but this site: [http://www.dlink.fr/?go=jN7uAYLx/oIJaWVUDLkZU93ygJVYKOhST9vhLPG3yV3oUo9/kP98f8p8Nqtm7z0vBS/pziVC+YwMA9w=](http://www.dlink.fr/?go=jN7uAYLx/oIJaWVUDLkZU93ygJVYKOhST9vhLPG3yV3oUo9/kP98f8p8Nqtm7z0vBS/pziVC+YwMA9w=) reveals it's probably true. :)

---

### Post by heimo on 2005-04-19
Oh, it's Dlink, not Linksys. That explains my confusion. Looks like the correct module is already loaded (you can check this with lsmod without parameters).
 
My conclusion is that it actually was correctly detected. You should probably look for instructions on howto configure wireless network. (search forum, check the FAQs - check iwconfig) 
 
And if you have any more questions, just ask. :)

---

### Post by mephisto56 on 2005-04-19
Thanks. Already busy reading man pages and searching through wikis etc. Seems like I'll need it. :)

---

### Post by az on 2005-04-19
You want to use ndiswrapper instead of the linux driver thatdoes not do WEP?

it is either the ac100 or the ac111 module for texas intruments wireless chipsets.

Your lspci shows it as the ac111.  Put that into /etc/hotplug/blacklist so that it is not automatically loaded.  You will then have to put ndiswrapper into your /etc/modules so that IT gets loaded.

Install your windows driver as described in the ndiswrapper documention.

---

### Post by nad on 2005-04-19
You've got the onboard ethernet controller turned on.

Go into your bios and disable it.

You may also wish to look here: [http://www.houseofcraig.net/acx100_howto.php](http://www.houseofcraig.net/acx100_howto.php)

Dan M

---

### Post by mephisto56 on 2005-04-19
> You want to use ndiswrapper instead of the linux driver thatdoes not do WEP? 

Do you mean the driver that comes with ubuntu isn't capable of wep? At least using the 'networking' tool I find there doesn't seem to work for me. Neither with wep, wap, or unencrypted. 

So I'm left with your option, using ndiswrapper, or nads, with that great tutorial link. Since some people have trouble with that last option I'll try ndiswrapper first. 

Thanks for all the help so far!

---

