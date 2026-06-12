---
title: "Resizing partitions...?"
date: 2005-12-29
forum: Installation &amp; Upgrades
---

### Post by eyce on 2005-12-29
Hello all,
 I screwed up a bit with my partitioning for ubuntu and have the following problem:

/ - root directory - has only 5.3 megs left in it, and the /lib directory which is a part of the /'s partition is the culprit.

Now the /tmp directory, which is a seperate partition on its own (at the end of the hard drive) is empty with lots of space to spare. 

I would like to resize the tmp so I can create another partition, then copy all of /lib into that partition and mount that partition as /lib. Is this doable without having to reinstall my linux system?

Thanks very much for all your help.

Best Regards and Wishes.

---

### Post by Herman on 2005-12-29
What types of partitioning software have you got that you can use?
:D (Herman)

---

### Post by az on 2005-12-29
[QUOTE=eyce]Hello all,
 I screwed up a bit with my partitioning for ubuntu and have the following problem:

I would like to resize the tmp so I can create another partition, then copy all of /lib into that partition and mount that partition as /lib. Is this doable without having to reinstall my linux system?
.[/QUOTE]

The easey peasey way of doing this is to change your fstab to mount /lib in that seperate partition and keep /var in your / partition.

You would have to copy everytying from lib to var there, unmount /var and remount it as /lib - after deleting everything there to liberate disk space.

To resize the partition, boot the installer and use parted from the command line (CTRL-ALT-F2 after the installer has detected your hardware)  You can delete that partition to free up some space, grow the partition just before it a little and then recreate your extra partition after that.   You can even do the above switch of var and lib by editing fstab and copying the files from the CTRL-ALT-F2 shell from the installer, if you like.

---

### Post by eyce on 2005-12-29
Azz.. You're a good man :).

Cheers! :)

---

