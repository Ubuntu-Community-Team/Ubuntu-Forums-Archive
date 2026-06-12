---
title: "Problems after installing Ubuntu 7.4"
date: 2007-10-12
forum: Hardware &amp; Laptops
---

### Post by Mr.Moo52 on 2007-10-12
I recently installed Ubuntu on my Dell laptop.  I decided to install it onto a USB harddrive so I could still have the full space on my laptop harddrive for windows xp.  I installed Ubuntu via the live CD with no problems and can boot to both Ubuntu and XP.  However, when I shutdown the computer and unplug the harddrive and then start it back up, I get a grub error, even though I'm not attempting to boot into Ubuntu.  Theoretically my laptop should forget that there was ever a USB drive on there and boot XP straight from the internal harddrive.  Once I plug the USB drive back in and reboot, it brings up the list of either Ubuntu or XP.  From there, they both boot fine.  What do I need to do so I don't have to lug this drive with me everywhere when I need to boot?

Mike

---

### Post by 5-HT on 2007-10-12
Uh oh...sounds like you installed grub to the master boot record of the internal drive.
Because of this, when you boot grub is looking for /boot/grub but there isn't one when the external drive isn't connected and it errors out.

It's an easy fix to overwrite grub from your MBR and replace the original windows bootloader: just pop in the xp disc and type 'fixmbr' from the recovery console.
After you do this, XP will boot just fine, but you'll loose grub.

I'd suggest that you then install grub onto the mbr of the external drive.
Here's info on how to do that, however, there are many different ways to do so: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

If you then go into your BIOS and allow booting from the external drive your computer will boot:

1. Straight into windows if the external drive is not connected
2. You'll be given a choice of windows or ubuntu when the external drive is connected (you may need to edit grub's config file to properly allow this please refer here for information: [http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)).


---------
There are many, many other ways of dealing with this issue and my suggestion is only one of them.

cheers,

---

### Post by Mr.Moo52 on 2007-10-13
Thanks for the info.  I haven't tried it yet as I'm away from my XP CD right now, but as soon as I get the chance, I'll do it and let you know what happened.

Mike

---

### Post by Mr.Moo52 on 2007-10-15
Well, I restored the MBR for Windows, and it seems to be working just fine.  I just need to do the stuff to get Grub on the Ubuntu partition and I'll be set.  Thanks for the help.

---

### Post by Mr.Moo52 on 2007-10-18
So, I was able to get grub back where it needed to be, but what bit of code do I have to edit to make it boot properly?  I was able to get to the grub boot menu when I booted from a USB device, but then it returned an error.

---

