---
title: "Moving to a new disk"
date: 2009-05-27
forum: Installation &amp; Upgrades
---

### Post by wootcat on 2009-05-27
My first install of Ubuntu was with 8. I chose the method to install Ubuntu on the same partition as Windows. I then updated to 9 and am now wanting to move Ubuntu to a new disk.

If possible I want to retain all the files/settings I currently have in Ubuntu (and Windows) and I want to continue to be able to dual boot between Ubuntu and Windows.

Is this possible? I could not see anything in the v9 documentation about installing/upgrading from a same-partition Ubuntu install. What is the best way to do this to a new disk?

Thanks!

---

### Post by wootcat on 2009-05-30
bump

---

### Post by wootcat on 2009-05-31
Anyone?

---

### Post by VastOne on 2009-05-31
> **wootcat said:**
> My first install of Ubuntu was with 8. I chose the method to install Ubuntu on the same partition as Windows. I then updated to 9 and am now wanting to move Ubuntu to a new disk.

If possible I want to retain all the files/settings I currently have in Ubuntu (and Windows) and I want to continue to be able to dual boot between Ubuntu and Windows.

Is this possible? I could not see anything in the v9 documentation about installing/upgrading from a same-partition Ubuntu install. What is the best way to do this to a new disk?

Thanks!

Yes.  You will first need to boot with a livecd and use gpart to create a partition on the new drive of equal size or more of your Ubuntu / (root) partition and format it to whatever flavour of ext you like. Once is it created, note what it is i.e. /dev/sdb1. Also note whatever the dev/ is of your current Ubuntu root i.e. /dev/sda1 or whatever

Once created go to Terminal and run 

```
dd if=/dev/sda1 of=/dev/sdb1

(change that to march your /dev setup)

```

This will create the exact partition of your root.


Once it is done you will need to run this in terminal

```
sudo tune2fs -U random /dev/sdb1 

(change to whatever is the new /dev/? partition)
```

That changes the UUID of the new partition because when you use dd to replicate it also replicates the UUID

Now you need edit your menu.lst and fstab to reflect these changes.

I just went through this at this thread

[http://ubuntuforums.org/showthread.php?p=7379586#](http://ubuntuforums.org/showthread.php?p=7379586#)

You need to be extremely careful and absolutely sure that you select the correct devices when using the dd command because it is capable of wiping out any partition if is incorrectly entered.

---

