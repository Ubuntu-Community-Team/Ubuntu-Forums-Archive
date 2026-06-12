---
title: "Error 22"
date: 2009-04-28
forum: Installation &amp; Upgrades
---

### Post by leonoel on 2009-04-28
Hello 

I have a laptop which ahs both vista and Ubuntu on it, but by mistake when I did the upgrade from a disk I put to use the entire HD to install linux, I figured out my mistake like 5 seconds later it started doing the partition.

Now I get error 22 of the grub, and the commands in the restore grub section do not seem to work.

Is my windows partition dead?
If it is, is there a way to recover my data??

Thank you

---

### Post by lovinglinux on 2009-04-29
Did you interrupted the installation in the first 5 seconds?

Most likely your Windows is gone, but there are some tools to recover data even after a format. Can help you with that tho.

Don't boot this machine from the hard drive until you get the data back. Use the Live CD if you need Internet access or to install recovery tools.

---

### Post by leonoel on 2009-04-29
Yes I totally interrupted it, well I turn off the PC itself.

If I want to get the data back, what should I do, like for example the live CD, I currently have the one of Ubuntu 8.04

---

### Post by lovinglinux on 2009-04-30
> **leonoel said:**
> Yes I totally interrupted it, well I turn off the PC itself.

If I want to get the data back, what should I do, like for example the live CD, I currently have the one of Ubuntu 8.04

You could try to boot from the Live CD and check if the Vista partition is still there. You can use GParted to do this.

If the partition is there, you could start Ubuntu from Live CD and backup the important data to a removable medium.

If the partition is not there, then you have to use a recovery tool. But as I said, I can't help you with that. Sorry.

---

