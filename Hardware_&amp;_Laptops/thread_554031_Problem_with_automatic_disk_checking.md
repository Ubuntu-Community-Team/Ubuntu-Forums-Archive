---
title: "Problem with automatic disk checking"
date: 2007-09-18
forum: Hardware &amp; Laptops
---

### Post by c_olin on 2007-09-18
I'm using the latest Ubuntu on an HP dv9000.  To my suprise everything is working great.  This is my first problem...

I have my swap set up on dev/sda3.  And after so many mounts it tries to automatically check it for errors on bootup.  But it locks up every time.  My other partitioned were checked fine, it is just dev/sda3 (my swap partition) where it freezes up.

How can I fix this?

Thanks

---

### Post by eggdeng on 2007-09-18
This thread explains how you can adjust / turn off this feature. [http://ubuntuforums.org/showthread.php?t=300477]("http://ubuntuforums.org/showthread.php?t=300477")
A better idea might be to download the gparted live CD and reformat your swap partition.

---

### Post by c_olin on 2007-09-18
Actually it turns out I was misunderstood.  /dev/sda3 is my /home partition.  So reformating it wouldn't be a good idea.

What are some of the causes of the fsck the lock up in the middle of the check?

---

### Post by c_olin on 2007-09-18
I ran fsck from a live cd and it fixed the problem beautifully.  

Problem solved... thanks

---

### Post by eggdeng on 2007-09-18
Your guess is as good as mine but it doesn't look like a good omen. I'd back up the partition just in case, then boot using the live CD and run ```
sudo fsck -y /dev/sda3
``` from a terminal.

---

