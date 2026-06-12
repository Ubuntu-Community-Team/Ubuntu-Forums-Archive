---
title: "Ubuntu won't detect LG DVD Writer"
date: 2006-12-22
forum: Hardware &amp; Laptops
---

### Post by nedsnow on 2006-12-22
Hi folks,

I tried posting this originally in the Absolute Beginner forum, but have had no luck, so I'll try here.

I am brand new to Ubuntu (but not Unix), and am having problems attempting to install. Ubuntu cannot detect my LG DVD Writer during the install, even though it boots from it, so I cannot proceed past the CD Mount step. I have gone through the forums and seen many others with the same problem, some with exactly the same drive, but no replies which offered a working solution to the problem.

I have tried both the Live CD and the Alternate CD, and neither work. Both CDs work fine on a Dell computer that I have, so it is not the CD.

My hardware is:
Asus P4S800 MB, SIS chipset (No SATA! It is not a SATA problem!)
ATI Radeon 9800 Display (It is not a display problem! It cannot detect the CD!)
1GB Ram.
80GB Drive on IDE0/Master
120GB Drive on IDE0/Slave
LG DVD Writer on IDE1/Master (HL-DT-ST DVDRAM GSA-4163B)

If I go to a shell and type "mount -tiso9660 /dev/hdc /cdrom"
it says Invalid Argument.

This command works on the Dell machine (if I unmount it first )

"list-devices cd" gives /dev/hdc

Someone suggested seeing if there is a firmware upgrade for the drive, but it's very difficult to upgrade the firmware because there is no version of Windows on this machine.

Is there any solution in sight? Anyone provide a clue?

Thanks in advance for any help.

Ned

---

