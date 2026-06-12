---
title: "Copying partitions?"
date: 2008-08-27
forum: General Help
---

### Post by Inane_Asylum on 2008-08-27
I had installed Kubuntu on a Vista machine with dual-boot and eventually deleted Vista.  So now I have 70G unallocated space *before* my Ubuntu partition.  I've tried just using the 70G part as my /home folder, and it's **almost** working.  And from what I've read, it's impossible/risky to move or resize a partition to the **left**.

Hypothetically speaking, if I couldn't get the /home partition thing fully working, would I be able to copy **all** the contents of my Ubuntu partition onto the first partition, edit GRUB, delete the second partition, and resize the first to the right?

I understand there may be problems like something in the filesystem refering to the partition by name (i.e. /dev/hda5) after I've copied everything to hda1...I dunno...that's why I'm asking :p

If all else fails, reinstalling and reconfiguring wifi/sound is always entertaining:popcorn:

---

### Post by Too Late on 2008-08-27
I've succesfully (or at least almost successfully) resized a partition to the left. I just wrote my experiences [here](http://ubuntuforums.org/showthread.php?p=5650694#post5650694).

And what problem did you have when you tried to use that as your home folder? There shouldn't be any problem.

---

### Post by Inane_Asylum on 2008-08-27
After using the psychocats tutorial for creating a /home partition, all of my settings reset...it looked like a fresh install, or at least a new user's desktop.  All configurations and settings were pfft. [Here's]("http://ubuntuforums.org/showthread.php?t=902345") the thread I started on that issue.

Best idea so far is that the .files didn't get copied, or permissions are screwy.

---

