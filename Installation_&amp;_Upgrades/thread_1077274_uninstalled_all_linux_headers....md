---
title: "uninstalled all linux headers..."
date: 2009-02-22
forum: Installation &amp; Upgrades
---

### Post by thpanis on 2009-02-22
Hello,

I accidentally uninstalled all linux headers (kernel?) on my Ubuntu 8.02 and now I can't start up Ubuntu through grub.

Does anyone know how I can solve this problem? Need help urgently!

Theo

---

### Post by veloce on 2009-02-24
> **thpanis said:**
> Hello,

I accidentally uninstalled all linux headers (kernel?) on my Ubuntu 8.02 and now I can't start up Ubuntu through grub.

Does anyone know how I can solve this problem? Need help urgently!

Theo

Deleting the headers won't do anything, deleting the kernel will.  It's now officially dead, you've killed it.

Use an install CD to re-install.  Make sure not to reformat anything you don't have - that will minimise the damage.

---

### Post by caljohnsmith on 2009-02-25
> **veloce said:**
> Deleting the headers won't do anything, deleting the kernel will.  It's now officially dead, you've killed it.

Use an install CD to re-install.  Make sure not to reformat anything you don't have - that will minimise the damage.
That's not true. It is possible to reinstall any uninstalled kernels to the Ubuntu partition using the Live CD. Theo, if you would like help doing that, how about opening a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
And please identify your Ubuntu partitions.

---

### Post by veloce on 2009-02-25
> **caljohnsmith said:**
> That's not true. It is possible to reinstall any uninstalled kernels to the Ubuntu partition using the Live CD. Theo, if you would like help doing that, how about opening a terminal (Applications > Accessories > Terminal) and post the output of:
```
sudo fdisk -lu
```
And please identify your Ubuntu partitions.

Sure it is - for a particular value of dead. :lolflag:

My question is, why not reinstall (and so reinstall anything else that has been deleted) to make a running system?

---

### Post by dmizer on 2009-02-25
> **veloce said:**
> My question is, why not reinstall (and so reinstall anything else that has been deleted) to make a running system?

Fixing is better than reinstalling for two very important reasons:
1) Reinstalling may overwrite important data.
2) Avoids the hassle of reconfiguring everything.

And one philosophically important reason: Reinstalling doesn't present a learning experience.

---

### Post by veloce on 2009-02-25
> **dmizer said:**
> Fixing is better than reinstalling for two very important reasons:
1) Reinstalling may overwrite important data.
2) Avoids the hassle of reconfiguring everything.

And one philosophically important reason: Reinstalling doesn't present a learning experience.

Well, other than the obvious ... :-)  

Actually, you have me intrigued, if I understand your solution it would run like:

Boot the live CD
copy the kernel from the CD to the right place on the hard drive.

Will you see the mount points of the partitions after booting with the Live CD?  Will they be mounted rw? (Hey - isn't that a security issue?)

Does this rely on the live CD having the same kernel version as was deleted?  (What would happen if they were different?)


(BTW, I try to only answer questions that I do know something about or that have been unreplied to for several days - I see this one was only two days old when I replied- my mistake.  

What is interesting is the number of times that I get a reply immediately when I respond to a question that has been sitting around for a week with no response!)

---

### Post by dmizer on 2009-02-26
> **veloce said:**
> Well, other than the obvious ... :-) 
Even the best of us need help with the obvious sometimes. I just spent an hour hunting down a busy hard drive which turned out to be a noisy fan :rolleyes:

---

