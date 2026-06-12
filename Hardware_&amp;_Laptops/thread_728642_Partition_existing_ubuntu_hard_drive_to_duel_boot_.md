---
title: "Partition existing ubuntu hard drive to duel boot windows"
date: 2008-03-19
forum: Hardware &amp; Laptops
---

### Post by StephanG on 2008-03-19
HI, I need to install windows for a program that won't run on wine.  Is it possible to partition my existing harddrive and install windows on it without losing my original linux data.  If so could anyone show me how?  I've got a kubuntu 7.04 live disk, but I don't know how to use qtparted for this task, help would be appreciated.

---

### Post by itix on 2008-03-19
Well first of all, the windows install will disable your Ubuntu partition (probably just because it is mean)

The [super grub disc]("http://supergrub.forjamari.linex.org/?section=download") is a wonderful tool that will restore your Ubuntu partition. Gnomes partition-tool Gparted let's you resize your existing partitions, but it doesn't always turn out ok. I don't know about qtParted since I've never used it, so that part I'll leave to someone else.

---

### Post by StephanG on 2008-03-19
Thanks,
seems worth looking into, how do I use the super grub disk?

---

### Post by itix on 2008-03-19
Just like when you install windows :p
Insert the disc and it'll restore your ubuntu partition. I don't use windows anymore so I don't have any use for mine. I did use it a couple of times when I still had windows though.

---

### Post by dark_phantom on 2008-03-19
You could install VirtualBox or VMware and install Windows as a virtual machine.  You'll be able to run Windows inside Linux side by side.  It's worth the try.

---

