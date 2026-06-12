---
title: "Damaged harddrive?"
date: 2006-01-31
forum: Installation &amp; Upgrades
---

### Post by h0bbe on 2006-01-31
Hi there!

After having some problem with my system I decided to format my harddrive and reinstall Breezy Badger. At the end of the installation I get the following messages:

"[563.384000] EXT3-fs error
(device hda1): ext3_free_branches: Read failure, inode = 700783, block = 1442451
[4295583.385000] Remounitng filesystem read-only"

When rebooting I get "Error 17" from GRUB.

My newbie-guess is that something is wrong with my harddrive. Some broken blocks maybe?? What can I do? Please help me!

---

### Post by az on 2006-01-31
From a live cd run

badblocks /dev/hda1 (assuming this is the correct partition)

---

### Post by h0bbe on 2006-01-31
Thanks for the quick reply, still no success though:

"badblocks: Permission denied while trying to determine device size"

...and I can't list the harddrive with "fdisk -l" either.

I'm getting ready to buy a new harddrive :-(

---

### Post by Ocxic on 2006-01-31
put sudo befor you commands to run them as root and see what happens.

---

### Post by h0bbe on 2006-02-01
:oops: It worked better with sudo...

Something strange happened though. After beeing away for a while (showering ;-)) the system had quit x (I guess) and had returned to the black command prompt (yes, I'm a newbie).

I didn't have time to try it again but what is the idea about badblocks, how is it going to help me?

Thanks for your help!

---

### Post by az on 2006-02-01
badblocks will print out any badblocks it finds.  It is not useful if the terminal in which you ran it dissapeared - I suspect this is your problem, and not neccessarily the HDD.

---

