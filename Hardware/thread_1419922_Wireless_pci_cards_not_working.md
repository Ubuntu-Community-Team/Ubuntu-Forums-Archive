---
title: "Wireless pci cards not working"
date: 2010-03-02
forum: Hardware
---

### Post by CyberJacob on 2010-03-02
I have two pci wireless cards, one generic acer, and the other i belive to be a D-link airplus G. nether of them work in my brand new ununtu instalation (9.10). i do not have much information on either the card or the pc as it is a collection of old parts.

---

### Post by coffeecat on 2010-03-02
You'll see from [this page]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCI") that D-Link PCI cards come with a wide variety of wireless chipsets - some work well, some don't. My D-Link AirPlusG had the ACX111 chipset which was such a stinker that I threw it out. Which doesn't necessarily mean that yours has. Let's hope not. I think AirPlusG is a generic tradename which says nothing about the chipset.

Put the PCI cards in one after the other, open a terminal and do:

```
lspci
```Look for the line that says "Wireless" or "802.11" and post that. Both of them - one for each card. Then we can see what chipsets you've got there, and what needs to be done to get them to work.

**Edit:** it probably won't do any harm to put both in at once (if you've got two spare PCI slots). That way you can get the information for both at the same time. The command 'lspci' merely lists all devices on the PCI buses.

---

### Post by CyberJacob on 2010-03-02
doesn't appear to be there, I put the acer card in but i couldnt find the d-link
 
```
00:00.0 Host bridge: Intel Corporation 82815 815 Chipset Host Bridge and Memory Controller Hub (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82815 Chipset Graphics Controller (CGC) (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 01)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 01)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82801BA/BAM/CA/CAM Ethernet Controller (rev 01)

```

---

### Post by coffeecat on 2010-03-02
You're right - it's not there. Have you another PCI slot? It's just possible that the PCI slot you've used is dead. If so, and you tested both cards in that one, that might explain why they won't work. So, try lspci with the Acer card in another slot if there is one.

If not, and you do find the D-Link, try the D-Link in the same slot and if nothing wirelessy appears in lspci then the PCI slot must be faulty.

---

### Post by CyberJacob on 2010-03-03
I have found the D-link card but the screws on the blanking plates for the other sokets are prity stiff, might take some time to crack it open but I should get it done by the weekend

---

### Post by CyberJacob on 2010-03-04
I fount the D-link card and put it in a different slot, it appears on lspci as:
```
RaLink RT2561/RT61 rev B 802.11g
```
i also put the acer card in but it causes the computer to hang when starting up, i tried all possible combinations and this is still the case however after carefull analasys of the hard I THINK I have identifyed it as a:
```
RTL8185L
```

---

### Post by coffeecat on 2010-03-04
From the information you've given, it seems as though the first PCI slot is faulty, so you'll have to use the second - the one you got the lspci output from.

Acer card - if it causes the computer to hang, that's enough reason not to use it. I've done a quick search of this forum and it seems others have had freezing systems with this Realtek chipset and difficulties getting it working. I have a PCI card with a different Realtek chipset, and performance is poor. Several reasons then not to use this card.

But the good news....

Your D-Link has a Ralink chipset - Ralink is usually very good in Linux and I've found reports that the RT2561 works just fine. I suggest you put the D-Link in the working PCI slot, boot up, click on the Network Manager icon and see if your wireless network is listed. If it is, just click on your network and put in your passkey where prompted.

Good luck!

---

### Post by CyberJacob on 2010-03-05
yay it works, i'm even posting from ubuntu!!!

---

### Post by coffeecat on 2010-03-05
Excellent! :)

---

