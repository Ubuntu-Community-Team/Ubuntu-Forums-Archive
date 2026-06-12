---
title: "Moving boot information to another hard drive"
date: 2008-07-12
forum: General Help
---

### Post by PureSamuel on 2008-07-12
Right. I have a laptop (60GB Hard Drive) with windows installed on it.
I recently bought a 500GB external hard drive, I then decided to try out linux for the first time and thought it would be logical for me to install it on my external hard drive and not risk messing anything up.
This is all fine, as my laptop rarely moves, however, every so often, I do move my laptop and can't use the hard drive due to a low amount of sockets or whatever reason. The problem is that without my hard drive, the computer wont boot into any OS.
I'm hoping to find a solution to move the boot information from the external hard drive (I assume that's how its working) to the laptop's hard drive.
Sam.

---

### Post by Lord Xeb on 2008-07-12
Make a /boot partition on the laptops hard drive and then copy over the boot from the external drive to /boot?

---

### Post by PureSamuel on 2008-07-13
Thanks for the quick reply.
How would I go about doing that?

---

### Post by fsmithred on 2008-07-13
You would probably use gparted to repartition the hard drive. There are many threads about that with good instructions. If you have Vista, you could use the partitioner that comes with it. You only need about 300MB or less for a boot partition. 

You'll also have to edit your /etc/fstab and your /boot/grub/menu.lst files to let the system know where the /boot partition is and to let grub know where to find the kernel. Lots of threads on that subject, too. 

Read up before you start hacking, and ask if something doesn't make sense.

---

### Post by PureSamuel on 2008-07-13
I've got XP and partition magic, so I'm good with partitioning
I think I'll leave it a while before I start moving stuff about
Thanks

---

