---
title: "I cant get my wireles to work! (broadcomm drivers, acer aspire 5024)"
date: 2007-02-07
forum: Hardware &amp; Laptops
---

### Post by l33cher on 2007-02-07
Hello,

i've been trying to get my wireless working for quite a long time now and damn i cant! I've got an acer aspire 5024 laptop and i've done everything that i could find in google. I downloaded the 64bit xp drivers and the ndiswrapper and did what i had to do. Then I downloaded the acer_acpi thing and did the echo enabled 1 thing too but nothing. I get this when i do my iwcofnig:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


i see something on eth1 but its not working, When i do the lspci thing i get:

00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 01)
00:02.0 PCI bridge: ATI Technologies Inc RS480 PCI-X Root Port
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:07.0 PCI bridge: ATI Technologies Inc Unknown device 5a39
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc Standard Dual Channel PCI IDE Controller ATI
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc ATI SB400 - AC'97 Modem Controller (rev 02)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X700 (PCIE)
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 Class 0805: Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)

I see it there but i dont know why its not working -.- if anybody has an idea what i'm doin wrong please tell me and help me solve this. Thanks in advance! P.S i get the APIC error on CPU0: 40(40) too. I'll keep searching for a fix and if i dont find one i'll post another thread here.

---

### Post by hakan69 on 2007-02-07
Hi!
I run Edgy on a Acer 5101, and this trick worked for my setup, perhaps worth trying. I installed Network Manager, and then made: 
sudo gedit /etc/network/interfaces (Perhaps wise to make a backup copy first) In this file I commented out all lines with a # sign except the lines:
auto lo
and the line staring with
iface lo ...
and then save and reboot.
I have no idea why it worked, I think it makes networkmanager take care of everything!

Regards/Hakan

---

### Post by sethjvm on 2007-02-07
I think you are going to need to provide some more information.  What exactly have you done to get where you are right now?

What happens when you type in "ndiswrapper -l"?

What about "lsmod"?

Did you edit the /etc/modules to include a line for ndiswrapper?

What does your /etc/iftab look like?

Did you blacklist the bcm43xx driver?

One of the biggest problems that I encountered with a Broadcom 43xG card was that it kept assigning the card to eth1 but the "sudo ndiswrapper -m" command appends ndiswrapper as wlan0.

---

### Post by Pistolpete2 on 2007-06-20
Look at this site [http://www.mumblyworld.info/index.php?post/2007/05/20/Wifi-sur-un-portable-Acer-Aspire-5024-wlmi-sous-Ubuntu-Gnu/linux-Feisty-Fawn-704](http://www.mumblyworld.info/index.php?post/2007/05/20/Wifi-sur-un-portable-Acer-Aspire-5024-wlmi-sous-Ubuntu-Gnu/linux-Feisty-Fawn-704) its a french site but I have a strong feeling it will work, I"m changing to feisty in a few days and I'm gonna use this resource. This is the place where I found the solution for my wireless under dapper drake.

greetings

---

