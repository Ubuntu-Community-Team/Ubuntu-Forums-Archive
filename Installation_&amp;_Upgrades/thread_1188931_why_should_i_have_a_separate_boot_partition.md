---
title: "why should i have a separate /boot partition"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by Gatemaze on 2009-06-16
Hi all,

is there any particular reason or benefit for having a separate /boot partition? I thought that the main reason is to be shared among different distros... but now that I am trying to test something a) it asks me to format the /boot (no go) b) i frankly i cannot see how the different images will be kept under the same directory... so what is the point of a separate /boot partition then?

Many thanks.

---

### Post by starfry on 2009-06-16
Some machines, older ones typically, could not boot from a partition bigger than (I think, 1024Mb). So you had to have a separate partition on a larger disk. I think that's the historic reason why people do this.

---

### Post by happyenduser on 2009-06-16
I read its used as a smart option on multiple OS's and Linux distros.

However, I've been having issues using a multi-boot GRUB on a separate BOOT partition - in relation to Windows XP. 
I realize that I just haven't found the right instructions to boot up XP yet; 
this has not been an issue for Linux OS's using a separate BOOT partition.

That is my own limited experience, as I am not 1337. :-\"

A very good primer on all things multi-boot is @ 
[http://members.iinet.net/~herman546/index.html]("http://members.iinet.net/%7Eherman546/index.html")

---

### Post by Gatemaze on 2009-06-16
Thanks :)

---

### Post by davidsrsb on 2009-06-16
I always use a ext2/3 /boot partition with root on JFS.
I have had boot failure in the past when I had everything JFS.
There are old reports of both JFS and XFS not liking Grub.
At the time there were stories that these file systems could dynamically move files on the disk and "suprise" the boot chain loader

---

