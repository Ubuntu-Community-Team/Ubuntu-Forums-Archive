---
title: "VAIO 13 Pro - Booting Troubles"
date: 2013-12-15
forum: Hardware
---

### Post by hans-klaufus on 2013-12-15
Hi all,

I have been trying to install UbuntuGnome 13.10 AMD64 on a Sony Vaio 13 Pro using a live version on a USB stick.
However, this seems to be a painful proces; without any succes yet.

I have googled around, and found many tips&tricks, but none seemed to work for me.

I have:
- disabled security boot
- enabled legacy mode
- changed boot order to boot from external device first.

First:
I installed Gnome-Ubuntu 13.10 **with** encrypted home folder.
Used boot-repair to fix the boot-process; and adding libata.force=noncq to the appropriate line.
This let to kernel panics as in the first attachment.

[ATTACH=CONFIG]248616[/ATTACH]

Next:
Tried to do the same, but then from UEFI mode, instead of Legacy mode.
This  seemed to make things worse - the Vaio13 would only start in its  'bios'-screens until the live usb was connected again and used.


Finally:
I reinstalled Gnome-Ubuntu 13.10 **without** encrypted home folder.
Used boot-repair to fix the boot-process ([http://paste.ubuntu.com/6577241/](http://paste.ubuntu.com/6577241/)); and adding *libata.force=noncq* to the appropriate line.
This let to a situation where, after grub loading, Busybox stops as per the second attachment - Gave up waiting.
I tried changing the UUID=1234566 to /dev/sda5, but this did not work either.
It seems that none of the disks are mounted / available (ls /dev shows a lot, but nothing that starts with sda*).

[ATTACH=CONFIG]248615[/ATTACH]

Hope you have some great ideas that help!

Thanks!
Hans.

---

