---
title: "Extra HD prevents booting."
date: 2006-03-01
forum: Hardware &amp; Laptops
---

### Post by Apo on 2006-03-01
Hi everyone,
please keep in mind that I'm a complete newbie on the Linux world.

My problem is as follows:
I installed linux without any problems, so that I have a dualboot system. After I assured that linux worked I installed another HD (maxtor diamondmax 10, 300gig, SATA), after which linux doesnt want to boot anymore (windows still works and accepts the disk).

When booting on linux I get the following text:
Savedefault
Boot
Uncompressing Linux... Ok, booting the kernel
Loading, please wait...
Alert! /dev/sda3 does not exist. Dropping to a shell.

Linux works when I remove the disk, but I dont really find that an acceptable solution. So what should I do to fix this? :???:

---

### Post by Apo on 2006-03-03
/bump :confused:

---

### Post by taurus on 2006-03-03
Well, is your first harddrive where Ubuntu is an EIDE or a SATA?  And you connect the second harddrive, how did you connect it?  From the error message at boot, it looks to me like Ubuntu is looking at the wrong harddrive for root's partition, /!  Maybe you need to paste a copy of your /etc/fstab here too...

---

### Post by Apo on 2006-03-04
The harddrive that contains Windows and Ubuntu is a sata disk, there are also 2 other discs attached: a SATA and an IDE. This is also why I find it very strange 1 extra disc gives problems.
I installed that one disc as you would any other: power off, attach cables, boot.

I dont seem to have a etc/fstab folder/file.

---

### Post by sadjack on 2006-03-04
taurus is right, somethings happening when you attach the extra drive. Without it the / system is seen properly, say at hda3, with it the bios is seeing the setup differently, so that / is perhaps on hda2 although its looking for it on hda3 which now contains soemthing completely different.

You will have have an /etc/fstab file, look carefully at the the syntax and include the first /.

I do not know how to alter things for you within linux, I'm sure there is some guru out there that can help. What I would do is to alter how the drives boot by changing the master / slave settings with the clips to see if that helps.

I do knlow the bios sees sata and ide drives at different times in the boot order and its that order that you need to change, again I would just try and experiment witrh different boot settings in nthe bios.

Hope this helps

---

### Post by Apo on 2006-03-07
I just made sure: I do not have an /etc/fstab file present. Another thing that seemed quite odd though is that I do have an /dev/sda3 file (doenst do anything though, not sure if thats normal :-? ).

Havent had time to fiddle with my bios so far though.

---

