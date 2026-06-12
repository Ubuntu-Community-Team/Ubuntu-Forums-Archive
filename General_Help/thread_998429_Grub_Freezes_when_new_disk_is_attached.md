---
title: "Grub Freezes when new disk is attached"
date: 2008-11-30
forum: General Help
---

### Post by leorob on 2008-11-30
I've been dual booting Ubuntu with Vista just fine for a while.  I recently got an e-SATA backup external drive.
When this drive is attached, the boot process freezes and I need to disconnect the drive, and after full boot, reattach the drive.

The same problem occurs if I install a new IDE drive in the system.  Windows would just boot up and say it found a new drive and all would be OK. However, GRUB doesn't seem to like any new configuration.

I assume GRUB is seeing a different configuration and therefore hangs up.

Is there a way to fix this?

Thanks,
a relative newbie

---

### Post by caljohnsmith on 2008-11-30
How many drives in total do you have? Have you set the Ubuntu drive to be first in your BIOS boot order? How about opening a terminal (applications > accessories > terminal), and please post the output of:
```
sudo fdisk -lu
```
Also, for each of the drives fdisk lists, like sda, sdb, etc, please post the output of:
```
sudo xxd  -l  2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
So replace "sda" above with each of your drives. Note "-l" is a lowercase L, not a one. And finally, for each command above that returns "eb48", please post:
```
sudo xxd -s 1049 -l 2 -p /dev/[COLOR="Red"]sda[/COLOR]
```
And replace sda with the drives that previously returned "eb48". That will greatly clarify what your setup is like.

---

### Post by leorob on 2008-12-01
While I'd be happy to do as you ask, I'm sure this info would be unrelated to my question.
This happens on any system I try to boot after attaching an additional disk.

I have only a single disk partitioned for Ubuntu and Vista. This boots with GRUB.  If another disk is placed in the system (for example to do a backup on) then GRUB does not complete.

---

### Post by caljohnsmith on 2008-12-01
When you say "Grub does not complete", what do you mean? Do you get a Grub error? What exactly happens on start up with the extra HDD attached? When you attach the extra HDD, have you checked your BIOS settings to make sure the Grub/Ubuntu drive is still first in the boot order?

---

### Post by leorob on 2008-12-02
With no external disk attached, boots fine into Grub menu.
With external disk attached via USB also boots fine.
With external disk attached via E-SATA GRUB gets to:

"Grub Loading stage 1.5.1
Grub Loading, please wait...
Error 22"

Bios is set to boot from "hard disk" first.

---

