---
title: "Reinstall Ubuntu error. No root file system(?)"
date: 2009-03-09
forum: Installation &amp; Upgrades
---

### Post by n1ahh on 2009-03-09
I followed instructions in other threads for reinstalling Ubuntu and hit an error that I do not understand. The situation is as follows.


Partitions:
/dev/sda      type       size           used
  /dev/sda1    fat 32    5239mb         4099mb
  /dev/sda2    ntfs      67077mb        44900 mb
  /dev/sda5    ext3      84654 mb       3000 mb
  /dev/sda6    swap      30067mb        0 mb

/dev/sdb  fat 32    8019 mb  753 mb

From the above I think the ubuntu is in /dev/sda5.  /dev/sdb is the thumb drive I am booting from. The computer is an Acer Aspire which has no CD/DVD so I am using a thumb drive as the boot source. No problem there.

I used the manual option and tried both the delete and edit options (independently of course) on /dev/sda5.  When I go to the next screen, I get the error 

"No root file system is defined. Please correct this from the partitioning menu."

I do not understand this. How should I proceed?

The problem is the result of trying to enable wifi hardware on an Acer Aspire. I followed the directions specified in another thread and it failed.  It also "broke" my USB ports under Ubuntu. I am dual boot as you can see and all is well under the xp partition.  I decided to reinstall ubuntu to get the usb ports working again before trying the wifi problem again. 

Any help appreciated.

---

### Post by Neo_The_User on 2009-03-09
Boot LiveCD and open up terminal

```

sudo fdisk /dev/sda
a
5
w

```

---

### Post by n1ahh on 2009-03-09
Thanks for the quick reply and assistance.

Tried fdisk as recommended. No change.

"When I did the Fdisk, I got the following error:
rereading the partition table failed with error 16: device or resource busy. the kernel still uses the old table. The new table will be used at next reboot"

I assumed this ment that the process would complete ok, but not be shown until the next reboot.

I rebooted, went to install and worked my way to step 4 which is the partition table. It held the same data as it did originally.  Partition 5 appeared unchanged.  I tried both edit and delete and got the same "no boot.." error. 

I repeated this process several times to verify my steps. Same result each time.

I rebooted into the ubuntu partition and it worked.  Fdisk did not seem to have an effect.

 So I am stick again at the same point in the process.

???

n1ahh

---

### Post by louieb on 2009-03-09
Just a wild guess that you chose the manual partition option. You need to click on sda5,  choose edit, and select / (root) as its mount point. Then you should be good to go.

---

### Post by Neo_The_User on 2009-03-09
Terminal from livecd:

```

sudo cfdisk

```

Take the boot flag off sdb. Use Up, down, right, left arrows to navigate.

---

### Post by Corbin Dallas on 2009-03-09
Why do you have a 30GB swap? Do you have TONS of memory available? or was this a typo?

In my experience, swaps should be 1 to 2GB.

30GB of swap may cause some issues.

---

### Post by Neo_The_User on 2009-03-09
> **Corbin Dallas said:**
> Why do you have a 30GB swap? Do you have TONS of memory available? or was this a typo?

In my experience, swaps should be 1 to 2GB.

30GB of swap may cause some issues.

Hahahaha! Yeah I didn't notice that before. Thats hilarious! 30GB swap! :lolflag: :biggrin: That would be... 15 GB of RAM to be exact. Must have one hell of a HP server computer!

---

