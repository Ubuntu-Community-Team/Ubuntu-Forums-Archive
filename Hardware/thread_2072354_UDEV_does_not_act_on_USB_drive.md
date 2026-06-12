---
title: "UDEV does not act on USB drive"
date: 2012-10-17
forum: Hardware
---

### Post by Bruno84 on 2012-10-17
Hello

I have a USB hard drive with two partitions.

The first one is mounted as /media/INTENSO without any problem.
The second one is encrypted with Truecrypt.

So I wanted to mount the second partition automatically with truecrypt.

```
ACTION=="add", KERNEL=="sd?1", ATTRS{serial}=="533252384A39414243313430", SYMLINK+="truecrypt", RUN+="/usr/bin/truecrypt --auto-mount=favorites"

```But udev does not seem to react when the drive is connected.

I put the output of "udevadm monitor" while connecting into the attachment.
Also I attached the ouput of "udevadm info -a -p /sys/block/sdd"

What can I do to solve that problem?

---

### Post by Bruno84 on 2012-10-18
It was necessary to do two things:

**SUBSYSTEMS=="usb",** had to be added to reach the right hierarchy spot for defining ATTRS{serial}.

And the password had to be written into the command, because udev can not open a query to get it.

>  ACTION=="add", KERNEL=="sd?1", SUBSYSTEMS=="usb", ATTRS{serial}=="533252384A39414243313430", SYMLINK+="truecrypt", RUN+="/usr/bin/truecrypt --auto-mount=favorites -p XXXXXX"

---

