---
title: "Using 2 HDD's fro Ubuntu"
date: 2009-02-21
forum: Installation &amp; Upgrades
---

### Post by roshanjose on 2009-02-21
I have 2 HDD's

1-->80GB
2-->160GB

I wanted to install Ubuntu and make both the disk access with a single installation of Ubuntu. I am planning to use VirtualBox and setup XP and OpenSolaris.

IS this possible?

Someone told me to setup a RAID 0?

What do you say?

---

### Post by jalvsmith on 2009-02-21
I posted the same question at the same time. I haven't thought much about virtual box though.  I'm looking forward to any answer you get.

Check my post to see if anyone posts there with relevant info for your situation as well.

[http://ubuntuforums.org/showthread.php?t=1076946]("http://ubuntuforums.org/showthread.php?t=1076946")

---

### Post by x33a on 2009-02-21
first of all i don't think there's any need for raid setup.

install ubuntu on either drive.

let's consider the 80gb drive.

1. 10-15 gb (user choice) ext3(root partition).
2. appropriate swap.
3. if you like a separate /home, then allocate the rest to /home. or simply format the rest with ext3.

4. format the other hard drive with ext3 as well.

now when ubuntu boots up, it should be able to see other partitions as well, and you can use them as you want.

afterwards you can install virtualbox and setup any os you want.

---

### Post by roshanjose on 2009-02-21
Thank you very much.

I am planning to setup XP and OpenSolaris on my VirtualBox.

I just thought of testing with OpenSolaris after I saw some professionals at Sun Microsystems using them.

What's your opinion of OpenSolaris and using virtualbox?

---

### Post by x33a on 2009-02-21
i haven't tried opensolaris myself, but i can say that virtualbox worked well with those i have tried.

---

### Post by roshanjose on 2009-02-22
ok

I just checked my repos.. there are virt-manager, virtualbox-ose...

dont know whether these are the right packages

---

### Post by x33a on 2009-02-22
install virtualbox-ose.

---

