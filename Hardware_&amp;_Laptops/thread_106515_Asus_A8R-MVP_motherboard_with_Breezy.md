---
title: "Asus A8R-MVP motherboard with Breezy"
date: 2005-12-20
forum: Hardware &amp; Laptops
---

### Post by n0fx on 2005-12-20
I was wondering if anyone had any experiences using Breezy with the Asus A8R-MVP motherboard?  It's fairly new and I was thinking of buying it and installing Ubuntu on it but I just want to make sure that the chipsets onboard work fine with Ubuntu.  It features the new ATI Radeon Xpress 200 CrossFire chipset with the ADI AD1986A SoundMAX for sound and the Marvell 88E8001 for the network card.

Basically I'm worried about the ULi M1575 south bridge, since I want to use the RAID5 functionality of the chip but I'm not sure if it's supported fully.  According to a page that I found, it says that it's supported through Fakeraid but has anyone actually tried this chip or board? The URL is here: [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

If anyone has any feedback regarding this board or any of its chipsets, please post it here.  I just recently got an Opteron 144 and was hoping to use the chip with this board for the RAID5 functionality.

Thanks :razz:

---

### Post by tnt63 on 2006-01-07
I have a running installation of Breezy on this motherboard, and have had no problems that I can directly relate to the south bridge. It detected my single SATA-disk without problems, don't know if things will be different with a RAID setup though. 
On the other hand I have had no luck getting the onboard NIC to work so far under Linux - it loads the skge module and sets up eth0 all right but never receives or transmits any packets. Got the system online by using an old wifi USB unit instead... I also had problems with my DVD-RW (Benq DW1640) during the installation and in fact had to replace it temporarily with an old CD-ROM to get the system installed.  Haven't gotten around to testing the DVD-RW yet after the completed installation, but suspect there could be problems. 
I think both of these problems (networking breezy with skge and installation problems with certain optical drives) have been described elsewhere in this forum, and so may be unrelated to the motherboard.

---

### Post by n0fx on 2006-01-10
[QUOTE=tnt63]I have a running installation of Breezy on this motherboard, and have had no problems that I can directly relate to the south bridge. It detected my single SATA-disk without problems, don't know if things will be different with a RAID setup though. 
On the other hand I have had no luck getting the onboard NIC to work so far under Linux - it loads the skge module and sets up eth0 all right but never receives or transmits any packets. Got the system online by using an old wifi USB unit instead... I also had problems with my DVD-RW (Benq DW1640) during the installation and in fact had to replace it temporarily with an old CD-ROM to get the system installed.  Haven't gotten around to testing the DVD-RW yet after the completed installation, but suspect there could be problems. 
I think both of these problems (networking breezy with skge and installation problems with certain optical drives) have been described elsewhere in this forum, and so may be unrelated to the motherboard.[/QUOTE]

Did you happen to try the sound card?  Mine seems to hang on the hotplug part of the bootup but I managed to disable it in the /etc/hotplug/blacklist file and it boots up but I'm still trying to figure out how to get the sound working, as well as the Marvell Yukon network card.

As for the raid, Ubuntu 5.10 doesn't detect the ULi bios raid, so I went ahead and made a MD instead.

---

### Post by tnt63 on 2006-01-10
No, I never got the soundcard to work either - and in fact ended up disabling it in BIOS since I was going to install another soundcard (Audigy 2) any way. I'm sorry to say that I gave up on Ubuntu for now - and am currently writing this from a newly installed Kanotix on the same machine. Hardware recognition seems better and the network card works... I'll try enabling the soundcard in the BIOS again and see if that works

;)

---

### Post by n0fx on 2006-01-13
[QUOTE=tnt63]No, I never got the soundcard to work either - and in fact ended up disabling it in BIOS since I was going to install another soundcard (Audigy 2) any way. I'm sorry to say that I gave up on Ubuntu for now - and am currently writing this from a newly installed Kanotix on the same machine. Hardware recognition seems better and the network card works... I'll try enabling the soundcard in the BIOS again and see if that works

;)[/QUOTE]

Yeah, let me know if it works. I will be trying to get both the sound card and network working.  If I figure it out, do you want to know how to do it?

---

