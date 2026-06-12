---
title: "swap hdd possible ?"
date: 2008-11-24
forum: Hardware
---

### Post by lucloubier on 2008-11-24
Hi !

I have a CDROM problem with one box. I would like to do the server install on one machine and then swap HDD afterwards. I plan to install/use one HDD only (I guess grub will work).

Is it possible to do so ? If so, anything I should be aware of ?

Thanks for your help...

---

### Post by renzokuken on 2008-11-24
in theory it is possible, but unless the machines have exactly the same hardware you might find it wont boot or you have to spend hours sorting out drivers and kernel modules.

a better option might be a Network Install. ubuntu has a wiki page on it [https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

alternatively, if your machine is capable of booting from a USB stick you could install it that way too [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

the USB install looks like the easiest way to go, but obviously depends on your machine being able to boot from USB (check the bios options to find out)

---

### Post by lucloubier on 2008-11-24
Not exactly the same motherboard...

I tried and the only thing that does not work is the network card.

Any clue on how to fix it ? ... step by step !

---

### Post by wgrant on 2008-11-24
Unless you're using a proprietary graphics driver, moving a hard disk between machines  of the same architecture should pose no problems whatsoever.

The problem you are encountering is simply the network interface name persistence machinery at work. It detects that your network card has a different MAC address, so probably calls it eth1 instead. If you have rules for eth0 in /etc/network/interfaces, that would be your problem.

To reset the name persistence, just remove the two interface lines that should be in /etc/udev/rules.d/70-persistent-net.rules.

---

### Post by lucloubier on 2008-11-25
Thanks wgrant !

Problem solved !

Any other tricks I should be aware of ...?

---

