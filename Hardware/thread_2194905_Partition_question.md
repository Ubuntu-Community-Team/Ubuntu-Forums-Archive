---
title: "Partition question"
date: 2013-12-21
forum: Hardware
---

### Post by michael-piziak on 2013-12-21
Currently I have Ubuntu on 200 megs and Vista on 50.
In the future, if I need the space, is it possible to get rid of the Vista and dedicate the entire HD to Ubuntu.
Or does one have to reinstall from the boot cd to do that.

---

### Post by ajgreeny on 2013-12-21
Certainly you can, as long as you installed the dual boot to separate partitions and did not use wubi to install it, which seems unlikely from your description.

If you do decide to go ahead, boot a live ubuntu DVD/USB and use gparted to delete the windows partition.  In theory you could try adding the space to your Ubuntu partition but it is probably better at the moment to leave the partition separate and use it for storage/data.  After deleting the windows partition run ```
sudo update-grub
``` from your ubuntu OS to remove windows from the grub menu.

---

### Post by michael-piziak on 2013-12-21
So if I boot with my Ubuntu 12.04 cd, I will get an option somewhere for "gparted" ?
I just tried it, and the initial option is to either try Ubuntu or install Ubuntu.  Do I click install and then somehow get to "gparted" ?  I guess I need baby steps to help me find gparted.

Then once I find gparted and repartition, take the cd out, boot, go to terminal, and type "sudo update-grub" ?

---

### Post by ajgreeny on 2013-12-21
No, no!

Use the **"Try Ubuntu without installing"** or whatever the wording of that option is.  It will end up with a desktop like a normal installation, but this time running from the DVD.  In the Dash you will find gparted and should use that to delete the windows partition.

If you're not certain of everything take a screenshot of the gparted window and attach it back here; use the paperclip in the toolbar of the reply window to attach the pic.

---

### Post by michael-piziak on 2013-12-21
I thank you for your knowledge.  At this time I'm going to leave the Vista on there, but in the future if I decide to eradicate it I will use this thread as reference.

Thanks!

---

### Post by michael-piziak on 2013-12-29
OK, today I booted with the 12.04 Ubuntu cd (dvd) and clicked "try ubuntu."
From the "Dash Home" I typed "gparted" and found that utility.

However, the utility looks hard to use.  What do I click to wipe out Vista and only have Ubuntu.
I'd like the entire HD to have Ubuntu, without losing what I have in Ubuntu now, and when the computer boots there is no option of which OS to go to - it just boots straight into Ubuntu without waiting 6 seconds to choose an OS.

---

### Post by Mark Phelps on 2013-12-30
We need to see what is on your drive before providing detailed instructions.

So, open a terminal, enter "sudo fdisk -lu" (lowercase L, not a one) and post the results back here.

This will allow us to confirm that this is NOT a Wubi installation.

---

