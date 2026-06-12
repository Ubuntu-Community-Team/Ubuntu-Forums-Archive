---
title: "samsung n150 sd card reader"
date: 2010-05-29
forum: Hardware
---

### Post by rell666 on 2010-05-29
I have got myself a samsung n150 netbook and im running ubuntu 10.04. got nealy everything working even got dual boot working with a bit of messing around and setpci sorted the screen brightness out. ndiswrapper sorted the wifi. the only thing that is not working is the sd card reader can anyone help?

---

### Post by d-wizzle on 2010-05-31
Hi rell666

I have the same set-up - an N150 with 10.04. I thought I had a problem with the SD card too, but trying again seemed to work. Sometimes it seems to take a long time to register: I often use some powertop suggestions for improving battery life, and one of these is a USB suspend so perhaps that doesn't help.

Have a look at the output of dmesg a few seconds after you've inserted it to see if there are any relevant USB messages. This evening I got two:

```
[  991.992182] usb 1-5: new high speed USB device using ehci_hcd and address 4
[  992.129348] usb 1-5: configuration #1 chosen from 1 choice

```
and it didn't seem to work: pulled it out and put it in again, and this time it did work with the proper messages in dmesg. It's a FAT32-formatted SanDisk 2GB card.

By the way - how are you managing screen brightness? I'm using a script called brightness.sh which has a setpci command in it. Do you have something more elegant than that?

Regards,

d-wizzle

---

