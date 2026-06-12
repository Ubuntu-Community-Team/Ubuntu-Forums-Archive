---
title: "Ubuntu 9.10 XD Card Reader Not Detecting Inserted Card on Acer 5050"
date: 2009-11-08
forum: Hardware
---

### Post by Renaud B. on 2009-11-08
Hi,

I'm using Ubuntu 9.10 and, although my 5 in 1 card reader seems to be detected, it doesn't detect if I insert a card or not in it (I'm using an XD card).

Here is some information from "lspci -v":
```
01:05.0 VGA compatible controller: ATI Technologies Inc RS482 [Radeon Xpress 200M]
	Subsystem: Acer Incorporated [ALI] Device 010f
	Flags: bus master, 66MHz, medium devsel, latency 66, IRQ 17
	Memory at c0000000 (32-bit, prefetchable) [size=256M]
	I/O ports at 9000 [size=256]
	Memory at b0100000 (32-bit, non-prefetchable) [size=64K]
	[virtual] Expansion ROM at b0120000 [disabled] [size=128K]
	Capabilities: [50] Power Management version 2
	Kernel modules: radeon, radeonfb

08:01.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
	Subsystem: Acer Incorporated [ALI] Device 010f
	Flags: bus master, medium devsel, latency 168, IRQ 23
	Memory at b0202000 (32-bit, non-prefetchable) [size=4K]
	Bus: primary=08, secondary=09, subordinate=0c, sec-latency=176
	Memory window 0: 40000000-43fff000 (prefetchable)
	Memory window 1: 48000000-4bfff000
	I/O window 0: 0000a400-0000a4ff
	I/O window 1: 0000a800-0000a8ff
	16-bit legacy interface ports at 0001
	Kernel driver in use: yenta_cardbus
	Kernel modules: yenta_socket

08:01.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 010f
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at b0203000 (32-bit, non-prefetchable) [size=128]
	Capabilities: [80] Power Management version 2

08:01.2 SD Host controller: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01) (prog-if 01)
	Subsystem: Acer Incorporated [ALI] Device 010f
	Flags: bus master, medium devsel, latency 64, IRQ 22
	Memory at b0203400 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

08:01.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 010f
	Flags: bus master, medium devsel, latency 64, IRQ 11
	Memory at b0203800 (32-bit, non-prefetchable) [size=128]
	Capabilities: [80] Power Management version 2

08:01.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)
	Subsystem: Acer Incorporated [ALI] Device 010f
	Flags: medium devsel, IRQ 22
	Memory at b0203100 (32-bit, non-prefetchable) [size=256]
	Capabilities: [80] Power Management version 2
	Kernel driver in use: sdhci-pci
	Kernel modules: sdhci-pci

```

When I insert or remove a card, nothing happens in Nautilus, neither anywhere in syslog, dmesg, etc.

How can I mount the card? What could the problem be?

Thanks for your time!

Note: My laptop is an Acer Aspire 3050-5050 with built-in 5 in 1 card reader.

---

### Post by jeebustrain on 2009-11-08
just for grins, leave the card in and reboot the box. I had this problem w/ my Toughbook - it would only detect the card when it was inserted at boot time. I could never figure out exactly why though.

---

### Post by Renaud B. on 2009-11-10
Hi,

Here it doesn't work, rebooting doesn't change anything.

Thanks anyway for your reply!

---

### Post by darkshadow on 2009-11-10
jeebustrain add "pciehp_pciehp_force=1" to the kernel options for Grub should fix that problem and let you insert a card at any time.

Renaud B. I don't think XD drivers for Linux are the best, probably because they are not the most common. But I have not really tried them in 3.5 years.

---

### Post by SIR_Arrentela on 2009-11-22
Hello , my Aspire One 110 is now with 9.10, but MS Cards is not working, like 9,04
MMC Card only work on rigth side
Anything i can do to help discover the problem?

My 9.10 is working good, but the memory cards still with any problem.

---

### Post by tiger2wander on 2009-11-28
> **darkshadow said:**
> jeebustrain add "pciehp_pciehp_force=1" to the kernel options for Grub should fix that problem and let you insert a card at any time.

Renaud B. I don't think XD drivers for Linux are the best, probably because they are not the most common. But I have not really tried them in 3.5 years.

thank you darkshadow, I've got my sd card reader again :popcorn:

---

### Post by DougR55 on 2009-11-28
> **tiger2wander said:**
> thank you darkshadow, I've got my sd card reader again :popcorn:
I am new to Linux Ubuntu and do not know how to add this line to the kernal options for Grub. Can someone give me a little help on this. My memory card reader is not functioning yet. 9.10 just installed.

---

### Post by kutturuvan on 2009-11-28
```
sudo gedit /boot/grub/menu.lst
```

Go to the line which shows some thing like this (this one is my case):

```


title		Ubuntu 9.10, kernel 2.6.31-15-generic
uuid		fe98eb72-9cf7-42bb-91b7-59abc2ab7f68
kernel		/boot/vmlinuz-2.6.31-15-generic root=UUID=fe98eb72-9cf7-42bb-91b7-59abc2ab7f68 ro quiet splash pciehp_pciehp_force=1


```

Insert the kernel option at the end of the line starting with 'kernel'.

I suppose this is correct. But it didn't work for me :(. Please let know if this works.

---

### Post by jetbelbes on 2010-03-19
Hi! I tried adding that to my kernel options but it didn't work.

I'm using an Acer AspireOne ZG5 and i'm trying to make the built-in memory card slot work. Could you please give me any suggestion on how to make it work? Thanks! :D

Here's what I did:

```
title		Ubuntu 9.10, kernel 2.6.31-20-generic
uuid		1973c604-09eb-4202-a86a-ae866d791ace
kernel		/boot/vmlinuz-2.6.31-20-generic root=UUID=1973c604-09eb-4202-a86a-ae866d791ace ro quiet splash pciehp_pciehp_force=1
initrd		/boot/initrd.img-2.6.31-20-generic
quiet
```

---

### Post by poltiser on 2010-04-18
I use Mint 8 64 on Aspire 5050 - card reader works - no problem...

---

### Post by Cornbreadly on 2010-04-19
> **SIR_Arrentela said:**
> Hello , my Aspire One 110 is now with 9.10, but MS Cards is not working, like 9,04
MMC Card only work on rigth side
Anything i can do to help discover the problem?

My 9.10 is working good, but the memory cards still with any problem.

I [found this thread.]("http://ubuntuforums.org/showthread.php?t=1308542")

I found mine in dev too.  Specifically,
```
/dev/disk/
```

Check there and look for something in the correct size range.  Mine is 4gb and I found it when I saw a folder with 3.9 gb available.  I will post back when I find something to help make it behave like removable media.

---

### Post by AnNyCoSa on 2010-10-19
> **tiger2wander said:**
> thank you darkshadow, I've got my sd card reader again :popcorn:


Hi! I'm just wondering if this works also with the "XD Cards"? I have no problem with "SD cards"...

05:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
        Subsystem: Hewlett-Packard Company Device 30f7
        Flags: bus master, fast devsel, latency 0, IRQ 11
        Memory at 97500000 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

Any detailed help would be so much appreciated!!! Thank you!!!

-I forgot to tell you that I have a Compaq notebook with the latest version of Ubuntu.

---

