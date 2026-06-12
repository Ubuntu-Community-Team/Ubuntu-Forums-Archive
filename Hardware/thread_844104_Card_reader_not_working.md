---
title: "Card reader not working"
date: 2008-06-29
forum: Hardware
---

### Post by NovaAesa on 2008-06-29
Hi all,

My problem is as follows:

I have a card reader in my laptop that doesn't appear to be working. When I put a card in, nothing obvious appears to happen. Here's the thing though. I'm not not really sure if the card I am using is compatible with the card reader. The card is an xD card, but on the front of the card reader only the following cards are listed: SD/MMC - MS/Pro. The odd thing is that the card fits into the slot perfectly and clips in just like it does in my digital camera. I'm thinking that either the card type is meant to be used with the card reader (and there's something I have to tweak in Ubuntu). *or* it is just a huge coincidence that the card happens to fit in perfectly.

Thankyou to anyone who can shed any light on my problem.

-Nova


EDIT: I forgot to add, my laptop is a Dell Inspiron 1525.

---

### Post by phidia on 2008-06-29
After you insert the card you can open a terminal and type > dmesg dmesg | tail will work too.
Usually at the end of the output there will be some info on recent activity.
I believe most card readers are just part of the usb system so ubuntu should be able to mount your card if it's mountable.
You can also type lsusb to see how many ports are available.

---

### Post by NovaAesa on 2008-07-02
Here's the requested outputs. I have no idea what they mean though, anyone care to interpret them for me?

```

ps@ps-laptop:~$ dmesg | tail
[112374.404595] wlan0: RX authentication from 00:18:d1:03:ac:a6 (alg=1 transaction=2 status=0)
[112374.404604] wlan0: replying to auth challenge
[112374.406133] wlan0: RX authentication from 00:18:d1:03:ac:a6 (alg=1 transaction=4 status=0)
[112374.406141] wlan0: authenticated
[112374.406146] wlan0: associate with AP 00:18:d1:03:ac:a6
[112374.407663] wlan0: RX ReassocResp from 00:18:d1:03:ac:a6 (capab=0x451 status=0 aid=1)
[112374.407671] wlan0: associated
[112374.407677] wlan0: CTS protection enabled (BSSID=00:18:d1:03:ac:a6)
[112374.449761] wlan0: CTS protection disabled (BSSID=00:18:d1:03:ac:a6)
[114262.191148] wlan0: CTS protection enabled (BSSID=00:18:d1:03:ac:a6)
ps@ps-laptop:~$ 

```


```

ps@ps-laptop:~$ lsusb
Bus 006 Device 002: ID 05a9:2640 OmniVision Technologies, Inc. 
Bus 006 Device 001: ID 0000:0000  
Bus 007 Device 001: ID 0000:0000  
Bus 005 Device 005: ID 0a5c:4503 Broadcom Corp. 
Bus 005 Device 004: ID 0a5c:4502 Broadcom Corp. 
Bus 005 Device 003: ID 413c:8126 Dell Computer Corp. 
Bus 005 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 005: ID 09da:022b A4 Tech Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
ps@ps-laptop:~$ 

```

---

### Post by karasuman on 2008-07-02
I'm having a similar problem with the same model laptop running Hardy.  I can stick an SD card in and read it fine, but memory sticks don't do anything.  I can, however, read memory sticks with a USB adapter; I don't know if that helps you at all, and it's still weird that we can't get the card reader to do its job.  I wish I could help, but I'm reduced to hoping someone helps you instead. :)

---

### Post by stchman on 2008-07-02
> **NovaAesa said:**
> Hi all,

My problem is as follows:

I have a card reader in my laptop that doesn't appear to be working. When I put a card in, nothing obvious appears to happen. Here's the thing though. I'm not not really sure if the card I am using is compatible with the card reader. The card is an xD card, but on the front of the card reader only the following cards are listed: SD/MMC - MS/Pro. The odd thing is that the card fits into the slot perfectly and clips in just like it does in my digital camera. I'm thinking that either the card type is meant to be used with the card reader (and there's something I have to tweak in Ubuntu). *or* it is just a huge coincidence that the card happens to fit in perfectly.

Thankyou to anyone who can shed any light on my problem.

-Nova


EDIT: I forgot to add, my laptop is a Dell Inspiron 1525.

I have a Toshiba laptop and it has a Ti 5 in 1 card reader.

If you have the same reader in your laptop then the drivers to read xD are not yet available.  SD cards work perfectly.

Give us an lspci output in this thread.

---

### Post by NovaAesa on 2008-07-02
> **stchman said:**
> Give us an lspci output in this thread.

```
ps@ps-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
02:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
02:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
02:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
02:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
02:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller (rev 12)
0b:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
ps@ps-laptop:~$ 
```

---

