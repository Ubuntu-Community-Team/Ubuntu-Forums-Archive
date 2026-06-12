---
title: "Boot mystery"
date: 2022-11-28
forum: Hardware
---

### Post by dinosaur1946 on 2022-11-28
Hi All

I have a Acer Swift 1 (au version) laptop that I wanted to take with me on a camping trip.
It has an internal Sd drive /dev/mmcblk0p1
Installed Ubuntu 22.04.1 LTS and it all works great.

To use it for software development I have a number of SSD's that when used with usb adapters will
boot on any other machine, but not on the Swift. Have tried everything from Freedos to Gparted Live.
There is no provision to specifically enable Legacy booting, only disable UEFI.

Yet here is the what I don't understand.
A live Debian USB will grab precedence and boot before Ubuntu.

I have been making bootable sticks with BalenaEtcher and can't understand the difference between
the Debian Live and for example the Gparted Live.

What do I need to do to force a boot priority ?
Pressing F12 for the boot menu only ever shows the internal SD.

Regards

---

### Post by oldfred on 2022-11-28
Have you updated UEFI from Acer?
[https://askubuntu.com/questions/1047065/fail-to-install-ubuntu-18-04-from-usb-to-a-brand-new-acer-swift-1](https://askubuntu.com/questions/1047065/fail-to-install-ubuntu-18-04-from-usb-to-a-brand-new-acer-swift-1)
[https://askubuntu.com/questions/862946/unable-to-install-ubuntu-on-acer-aspire-es1-533](https://askubuntu.com/questions/862946/unable-to-install-ubuntu-on-acer-aspire-es1-533)

External drives boot from /EFI/Boot/bootx64.efi. Description in UEFI is then the name or label of the external drive.
 
But a full install of Ubuntu to an external drive installs the standard internal drive boot of /EFI/ubuntu/shimx64.efi to the ESP on the internal drive. External drive then is default boot, but must always be connected.

  [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Others suggest disconnecting all other drives physically or logically in UEFI settings, so install drive is first drive.
Or removing boot flag/esp flag from first drive, so only ESP is install drive.
Or if you have ESP on second or external drive, you can just reinstall grub, either manually or using Boot-Repair's advanced mode & full reinstall of grub to correct drive. 

To fully understand boot and where you have files you can run Boot-Repair's Summary Report. 
I periodically run it just to document my system and save report in /home so backed up.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by dinosaur1946 on 2022-11-29
Hi

Many thanks for your reply.

The core of the issue appears to be the Acer Swift 1 and one you migrate away
from Windows.

You can't even update your BIOS without Windows, definitely NOT going there.

I have a Panasonic ToughBook which will boot on every USB OS I can throw at it.
So I won't make career out of trying to fix a $400 laptop.

Appreciate your time in replying

Regards

---

