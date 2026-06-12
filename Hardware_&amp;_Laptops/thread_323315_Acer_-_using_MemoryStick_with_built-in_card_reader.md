---
title: "Acer - using MemoryStick with built-in card reader"
date: 2006-12-21
forum: Hardware &amp; Laptops
---

### Post by Timokl on 2006-12-21
Hi there,

I have an Acer Aspire 5020 notebook which has a built-in card reader from Texas Instruments. This device worked out of the box - but only with SD cards.

However, I would like to use it with a MemoryStick to upload podcasts to my Sony Ericsson P910i. I could use Bluetooth, but this takes ages for bigger files. :( 

But if I pop the phone's MemoryStick into the card reader, it does not get mounted, but the kernel detects that there has been put something into the device:

```
timo@aristoteles:/dev$ dmesg | tail
[17181057.996000] SGI XFS Quota Management subsystem
[17181058.108000] JFS: nTxBlock = 4019, nTxLock = 32158
[17181076.044000] usb 3-2: USB disconnect, address 4
[17181079.896000] tifm_7xx1: demand removing card from socket 2
[17181087.108000] tifm_7xx1: **sd card detected in socket 3**
[17181088.332000] mmcblk0: mmc3:5c9b S064B 62080KiB 
[17181088.332000]  mmcblk0: p1
[17181091.200000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17181104.420000] tifm_7xx1: **demand removing card from socket 3**
[17181109.880000] tifm_7xx1: **ms card detected in socket 2**
```

The SD card I put into socket 3 is detected and mounted, but the MemoryStick is merely detected at socket 2.

Here are some information about my card reader device: 
```
timo@aristoteles:/dev$ lspci | grep Texas
06:06.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller
06:06.2 FireWire (IEEE 1394): Texas Instruments OHCI Compliant IEEE 1394 Host Controller
06:06.3 Mass storage controller: Texas Instruments PCIxx21 Integrated FlashMedia Controller
06:06.4 Class 0805: **Texas Instruments PCI6411, PCI6421, PCI6611, PCI6621, PCI7411, PCI7421, PCI7611, PCI7621 Secure Digital (SD) Controller**
```

I don't mind mounting by hand using a terminal. So, anyone with an idea how to access this MemoryStick???

Thnx!

Bye, Timo

---

### Post by |ferrari| on 2006-12-23
Try this out:

```

sudo modprobe tifm_sd
```

Use a memorystick to test it. If it works:
```
sudo getdit /edit /etc/modules
```

add this in a new line:
```
tifm_sd
```

This works for me on a Acer Ferrar 4005! ;)

---

### Post by Timokl on 2006-12-24
> **|ferrari| said:**
> Try this out:

```

sudo modprobe tifm_sd
```

Use a memorystick to test it. If it works:

Thnx |ferrari| for your hint. Sadly, it did not work. :( 

The kernel module for my computer seems to be the tifm_7xx1 module which seems to be a different one from the tift_sd. But anyway, perhaps I will find some information on it.

Thnx!
Timo

---

### Post by Timokl on 2006-12-24
OK, I did a little research on the net, and I came up with the following:
[LIST=1]
[*]MemoryStick seems to work, but MemoryStick Pro does not seem to work yet (which is the device I would like to mount) [http://ubuntuforums.org/showthread.php?t=311914]("http://ubuntuforums.org/showthread.php?t=311914")
[*]As usual, the hardware data sheet by the card reader's manufacturer had not been publicised completely.
[*]There is an alternative development for a kernel module, see: [http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver]("http://openfacts.berlios.de/index-en.phtml?title=TI_FlashMedia_xx12/xx21_driver")
[/LIST]

Seems like I have to wait and see what's going to happen with the coming development. :neutral: 

But anyway, there seems to be progress. :D

---

