---
title: "Minicomputer refuses to start Focal Fossa, after years of faultless service"
date: 2021-09-11
forum: Hardware
---

### Post by logie on 2021-09-11
I have been using an Intel NUCminicomputer for several years. It has Intel Core i3 X4, running Ubuntu, most recently distro20.04 (Focal Fossa).

a week ago it refused to start.  It shows the following messageon screen:
..........................................................................................................................


[FONT=Liberation Sans, sans-serif]/dev/sda2contains a filesystem with errors check forced.[/FONT]
[FONT=Liberation Sans, sans-serif]Inodesthat were part of a corrupted orphan linked list found.

[/FONT]
[FONT=Liberation Sans, sans-serif]dev*/*sda2:UNEXPETEDINCONSISTENCY:RUN fsck MANUALLY.[/FONT]
[FONT=Liberation Sans, sans-serif]	
(i.e.,without -a or -p options)

[/FONT]
[FONT=Liberation Sans, sans-serif]fsckexited with status code 4[/FONT]
[FONT=Liberation Sans, sans-serif]Theroot filesystem on /dev/sda2 requires a MANUAL fsck[/FONT]


[FONT=Liberation Sans, sans-serif]		BusyBox v 1.30.1 (Ubuntu 1:1.30.1-4 ubuntu6.3
[/FONT][FONT=&quot]built-inshell (ash)[/FONT]
[FONT=Liberation Sans, sans-serif]
Enter‘help’ for a list of built-in commands.[/FONT]
[FONT=&quot]
(nitramfs)
....................................................................................................................[/FONT]



Ientered ‘help’ and got a 10-linelist ofcommand words, which did notmean very much to me.


I’d be grateful for anyadvice.  I have little understanding of the inner workings of Linux,but manage to follow instructions as a rule.


Thank in anticipation.


logcx

---

### Post by Doug S on 2021-09-11
It looks like your disk is broken.

---

### Post by tea for one on 2021-09-11
Perhaps boot into a live Ubuntu session and run fsck on /dev/sda2?

---

### Post by ajgreeny on 2021-09-11
To give you more info just in case **tea for one**'s suggestion does not mean much to you, boot to a live ubuntu system, eg on a USB as you did perhaps when you installed originally, open a terminal and in that run command ```
sudo fdisk -l
``` to confirm the device name for the root partition of your installed OS is /dev/sda2.

Once you are sure which is the root partition run command ```
sudo e2fsck /dev/sda2
```
With luck that will show you some errors and offer to repair them.

Good luck.

---

### Post by logie on 2021-09-13
> **Doug S said:**
> It looks like your disk is broken.


Thanks for your reply, but why do you think that?  I'd not want to try replacing the SSD unless I could be sure.

---

### Post by logie on 2021-09-13
> **ajgreeny said:**
> To give you more info just in case **tea for one**'s suggestion does not mean much to you, boot to a live ubuntu system, eg on a USB as you did perhaps when you installed originally, open a terminal and in that run command ```
sudo fdisk -l
``` to confirm the device name for the root partition of your installed OS is /dev/sda2.

Once you are sure which is the root partition run command ```
sudo e2fsck /dev/sda2
```
With luck that will show you some errors and offer to repair them.

Good luck.

Thanks for this help.  Could you please explain a little more:  you say 'boot to a live ubuntu system'.  I cannot at present boot to anything on the microcomputer that is causing trouble.  Can I boot on a different machine?  (or what? )
I shall certainly need luck!
 greetings, logie.

---

### Post by tea for one on 2021-09-13
I suspect that your installed Ubuntu file system is damaged, which prevents you booting cleanly.

However, it will (hopefully) not prevent you booting a live Ubuntu session, similar to when you installed Ubuntu in the past.

Here is some info:- [https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started](https://ubuntu.com/tutorials/try-ubuntu-before-you-install#1-getting-started)

You may need your different machine to download the ISO and make a bootable USB device.

---

