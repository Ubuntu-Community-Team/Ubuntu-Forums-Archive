---
title: "USB Multicard reader not recognised"
date: 2011-01-21
forum: Hardware
---

### Post by HappyLinux on 2011-01-21
I've got a USB card reader that doesn't get recognized, not even a message that a new piece of hardware is detected, but cannot find drivers for it.

It works great under Windows.

The reader is a basic unbranded one, but it can handle something like 30 different card types. Well, that might be exaggerating a little. It's got 5 different slots. As far as I know, it can handle SD, MSPro, MMC with their variants, and a couple other slots that I cannot remember.

The reader also acts like another USB Hub, as it has 3 USB2 sockets built into it.

If anything, just plugging it in, Ubuntu should detect it as another hub.

I tried plugging it in and then connected my mouse into it. For a moment, it recognizes the mouse, but then trips out. I think the sockets have gone on it. However, the card reader part still works under Windows.

I tried inserting an SD card and an MSPro, but neither is detected under Ubuntu.

Is there something I'm missing?

---

### Post by HappyLinux on 2011-01-23
Can anyone help me with this?

---

### Post by dandnsmith on 2011-01-23
For elimination purposes: is the Windows installation you tested on the same PC as the Ubuntu? (I'm wondering about a dodgy connection somewhere).

My simple minded approach says that something must get detected if the mouse is seen, even momentarily.

Does anything show up in lsusb when it's plugged in (the card reader, that is).

---

### Post by HappyLinux on 2011-01-24
yes, it's a dual-boot system.

what is Isusb? I'm guessing it's something to do with USBs.

sorry, I'm still a newbie with Lunix. I've only just started learning the basics of Linux command-line.

---

### Post by dandnsmith on 2011-01-24
That is Lsusb, only with a small ell.
Lists the usb hardware and attached stuff.

---

### Post by HappyLinux on 2011-01-25
how do I find this lsusb?

---

### Post by 0N3 on 2011-01-25
Open a terminal and type lsusb into it to list your usb devices hence "lsusb"

---

### Post by HappyLinux on 2011-01-25
I plugged the car reader in and then did the lsusb. here are the results, freshly copied from terminal

Bus 002 Device 009: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 008: ID 058f:6254 Alcor Micro Corp. USB Hub
Bus 002 Device 007: ID 046d:c043 Logitech, Inc. MX320/MX400 Laser Mouse
Bus 002 Device 006: ID 045e:00db Microsoft Corp. Natural Ergonomic Keyboard 4000 V1.0
Bus 002 Device 005: ID 0411:0105 MelCo., Inc. 
Bus 002 Device 004: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by 0N3 on 2011-01-25
According to that output the card readers being recognised

---

### Post by HappyLinux on 2011-01-26
then can anyone let me know how to get it working please?

---

### Post by ajgreeny on 2011-01-29
There seem to be several bugs and posts in launchpad and the ubuntuforums about this Alcor Micro Corp. Multi Flash Reader.

What have you tried already?  And are you sure it's not a strange filesystem on the card you are trying to read, as was the case in one instance I found; a nokia phone file system, not recognised by ubuntu.

There are also sevaral cases where an SDHC card was being tried, which many older readers will not accept.

---

### Post by HappyLinux on 2011-01-30
The reader I have was a cheap one that I picked up from a supermarket. On the underside, it says that it's an AGK, model 10246. It's apparantly an 18in1 reader.

All the cards I have tried are formatted with FAT32.

The cards I have are a 1GB MSPro and a 2GB MicroSD through an SD adapter. I haven't tried my MSPro Duo card as that is currently in my PSP which is being borrowed by my sister. I've thrown away a couple of old SD cards because they were so small in capacity. A 32MB and a 64MB I think.

---

