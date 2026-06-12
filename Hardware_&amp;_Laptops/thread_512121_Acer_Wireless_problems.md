---
title: "Acer Wireless problems"
date: 2007-07-28
forum: Hardware &amp; Laptops
---

### Post by Doodlemepink on 2007-07-28
Hi,
Im Really new to Linux. Im using Ubuntu Fiesty and i cant seem to get my wireless to work. I have searched the forums like a good boy beafore posting my own thread. I have tried Ndiswrapper, and I can not get that to work. I have tried to compile the kernal for my wireless card (2200bg) and that wont work. Network manager detects my card, and i think its working but it is not showing anywireless networks or letting me conntect to any. 
I got the read out from the machine... I read somthing about turning the wireless card on in the bios or having to compile a program to do it.. but i cant seem to get that to work either... 
any help or a point in the right direction would be greatful. Im about to strangle myself with this CAT5. 
Again Im a complete newb. so step by step and slow. Pleas forgive my ignorance.
 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:01.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG Network Connection (rev 05)
06:08.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 02)


EDIT::
Using   'iwlist scan' i got this.

eth1      radio off  ESSID:""  

 Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

I think if i can turn the card on then i will have it.
Any Ideas?
I'll keep looking and post any answers that I find.

---

### Post by ugm6hr on 2007-07-28
> **Doodlemepink said:**
> 
eth1      radio off  ESSID:""  

I think this means it's turned off from BIOS.  

Does the laptop have a switch to turn wifi on at the front?  Worth trying that first.  

If that doesn't work - go into BIOS (at startup of computer) - I think F12 or F2 for Acers, and ensure that it is not turned off there.

You do not need ndiswrapper - the 2200bg is one of the best supported wifi chipsets in linux.  It should work out-of-the-box (if it is turned on!)

---

### Post by Doodlemepink on 2007-07-29
There is no option in my BIOS for that, and the button doest work... But i went to a website, and they installed a driver... i forgot what the URL was.. Im going to go look it up... but they did the whole thing online. it was sooo easy.. ill update with the url..

---

