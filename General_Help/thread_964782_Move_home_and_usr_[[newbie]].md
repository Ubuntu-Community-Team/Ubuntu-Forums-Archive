---
title: "Move /home and /usr [[newbie]]"
date: 2008-10-31
forum: General Help
---

### Post by pingtiao on 2008-10-31
Hi there.

I am new to ubuntu.
When I set it up for the first time, I assigned the lions share of my home drive to /usr, as I thought this would be the directory that took the most space.
I now know that this should have been /home.

I now want to move home to the big partition, and move /usr back to the main one.

> mark@mark-desktop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             9.3G  6.9G  2.1G  78% /
tmpfs                1012M     0 1012M   0% /lib/init/rw
varrun               1012M  324K 1012M   1% /var/run
varlock              1012M     0 1012M   0% /var/lock
udev                 1012M  2.8M 1010M   1% /dev
tmpfs                1012M  1.1M 1011M   1% /dev/shm
lrm                  1012M  2.0M 1010M   1% /lib/modules/2.6.27-7-generic/volatile
/dev/sda5             194G  4.4G  181G   3% /usr
overflow              1.0M  128K  896K  13% /tmp
/dev/sdb1             153G   86G   68G  56% /media/durruti


As you can see here, /usr is on sda5, and home on sda1.
I want to switch these as I'm running out of space.

I tried doing the 'move home' tutorial from psychocats, but this borked everything and I had to revert.

Please help!

---

### Post by francisc1701 on 2008-10-31
This is how I'd do it:

1. First of all, check your /etc/fstab to see if your partitions are identified by their uuid. If they are, run ```
sudo blkid
``` that will list all the partitions and their corresponding UUIDs. Write that down somewhere.
If the partitions in /etc/fstab are identified by their device name (/dev/hda), not by uuid then steps 3 and 4 are not necessary.

2. Boot the ubuntu livecd and use GParted to resize the partitions you want.

3. When you're done resizing the partitions, run ```
sudo blkid
``` again and compare its output to the one you wrote down at step 1. If you see any differences, use tune2fs to change the uuids back to the old ones you wrote down. ```
sudo tune2fs -U <uuid>
```

4. Run ```
sudo blkid
``` again to make sure all uuids are the way they were before you resized anything.

(I had resized my swap partition and the next thing I knew I couldn't hibernate, because the swap partition's uuid had changed after resizing.)

I hope I didn't forget or mistype anything.
Good luck!

---

### Post by pingtiao on 2008-10-31
Thaks for that.

How do I actually copy the data from home over to the new partition, copy the data for usr back to the main partition, and point intrepid to the new partition for home?

---

### Post by francisc1701 on 2008-10-31
If all you want to do is resize YOU don't have to copy any data from any partition. GParted does that for you. I you do it the way I said you won't be creating any new partitions, nor deleting any old ones. You'll just resize them. Your partitions will remain the same, only they'll have different sizes.

GParted should preserve all the data on your partitions. It did every time I used it.

Do you want to move /usr back to the root partition (/dev/sda1)? Please specify, 'cause I don't wanna write the instructions unless you need them. (lazy type :) ) Also, do you want to have a separate partition for /home ? I mean, once you resize /dev/sda1 you might have enough space there.

---

### Post by pingtiao on 2008-10-31
Thanks for the reply.
Yes, I want to move /usr back to sda1, and then move home to /sdb1
I don't want to resize either partition, just move the assignations between them (I've already resized to what I want, I just assigned /usr to the big partition when it shoould have been /home)

---

### Post by francisc1701 on 2008-10-31
> Yes, I want to move /usr back to sda1, and then move home to /sdb1
Ok. But /usr seems to be 4.4G, while / only has 2.1G available:
> Filesystem Size Used Avail Use% Mounted on
/dev/sda1 9.3G 6.9G 2.1G 78% /
/dev/sda5 194G 4.4G 181G 3% /usr
/dev/sdb1 153G 86G 68G 56% /media/durruti
That leaves you two choices: 1. you leave /usr where it is; 2. you resize /dev/sda1 first (adding another 10G should do), then move /usr.

I just copied my home directory to /tmp using konqueror and it seems to have worked, including hidden files. I suppose Nautilus can do it as well.

---

