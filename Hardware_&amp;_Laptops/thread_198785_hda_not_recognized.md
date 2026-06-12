---
title: "hda not recognized"
date: 2006-06-17
forum: Hardware &amp; Laptops
---

### Post by Footer on 2006-06-17
Need some help here folks ... Big storm went through last night.  I leave my machines running 24/7 but probably was a mistake this time ...

Went to reboot my Kubuntu Dapper Drake and no go.  Got the GRUB error 17.  After much investigation, I've come to the conclusion that the boot record must be toast.  I can see my partitions with fdisk:

[COLOR="Blue"]Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1541    12378051   83  Linux
/dev/hda2            1542       19457   143910270    5  Extended
/dev/hda5            1542       19132   141299676   83  Linux
/dev/hda6           19133       19457     2610531   82  Linux swap

Command (m for help):[/COLOR]

But can't figure out how to get to them.  Kubuntu Live CD won't boot up the machine nor will several other live distros I have laying around with the exception of one:  PCLinuxOS.  It shows the disk but I can't get to it!  So does this mean GRUB is gone/corrupt?  Unfortunately, PCLinuxOS uses LILO which I'd use if I could figure out how.

Basically looking for a way to get back to my hard disk with out starting over.  I have a 2nd disk in there and it's fine (hdb).

Any and all help is GREATLY appreciated!

:)

---

### Post by Footer on 2006-06-19
Thanks to the latest Knoppix distro, I've determined that my 160GB disk has gone (or is going) BAD!  Knoppix detected it, said it's failing and to backup IMMEDIATELY.  I found the only partition I could get to was /dev/hda5 (after multiple power cycles) which as luck would have it was my HOME partition!  I had backed it up the night before so only would have lost what little I did that morning but anyway, I have it in it's final form.  The other partitions were not mountable.  I/O errors galore ...

New 250GB disk is on it's way ...

:)

---

### Post by Lord Illidan on 2006-06-19
Try running fsck on the disks. Best cure to this is prevention, however, read weather forecasts. If storms are predicted, switch off and unplug. Consider getting a surge protector, too.

---

### Post by Footer on 2006-06-19
Thank you Lord.  :-)  I will try fsck on the disk.  And you're right, this could have been prevented in the first place.  I have surge protectors and a UPS but they're OLD.  Time to replace both.  Got a new surge protector coming with the new hard disk and considering purchasing a new UPS as well ... SOON.  Summer is here and with it comes thunderstorms ... and the power in our neck of the woods is not so reliable.

Thanks for the reply!

:)

---

