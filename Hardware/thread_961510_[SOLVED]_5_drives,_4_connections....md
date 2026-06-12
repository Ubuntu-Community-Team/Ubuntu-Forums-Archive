---
title: "[SOLVED] 5 drives, 4 connections..."
date: 2008-10-28
forum: Hardware
---

### Post by Cowzor on 2008-10-28
Hey guys,

I've got an old computer I'm turning into a small webserver. I've got a bit of a problem though. Being the age that it is, it only supports 4 IDE connections, and there are 4 hard drives inside it. So if I want to install ubuntu I need to disconnect one of the harddrives so that I can hook up the CD drive. This means that while installing ubuntu I can't mount any of the root folders onto the disconnected harddrive (I want /var on one drive, /home on another, /usr on the third and everything else on the fourth drive).

Can anyone help me out with this problem?

Many thanks in advance.

---

### Post by caljohnsmith on 2008-10-28
If I were in your shoes, I might remove the drive you want to put /home on, go about your Ubuntu installation and let /home be in your root "/" partition, and then afterwards move /home over to the other drive once you are done. I believe there is even a psychocats tutorial on moving the /home partition, and it's not usually hard to do at all. Basically you just move /home over and update your /etc/fstab to include the new /home partition mount point. If you want more details, let me know, but that's the general idea. :)

---

### Post by Cowzor on 2008-10-28
Thanks! yeah, I do get what you're saying. I'm just stuck to the terminal though (server edition), what terminal command do I use to move the /home folder to a different partition, and what exactly should I be editing in /etc/fstab?

---

### Post by caljohnsmith on 2008-10-28
OK, let's say your home partition is sdb1, and you've booted into your main Ubuntu install which currently has the /home directory. You could do:
```
sudo mkdir /media/sdb1
sudo mount /dev/sdb1 /media/sdb1
sudo cp -ax /home/* /media/sdb1/.
sudo mv /home /home.backup
sudo mkdir /home
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
```
And add these lines in your fstab:
```
#/dev/sdb1:
UUID=77677cb5-6e56-4936-a373-80c15e /home ext3 nodev,nosuid 0 2
```
And of course replace the UUID above with the UUID of sdb1, which you can find with:
```
sudo blkid -c /dev/null
```
Once you confirm that everything works OK, you can get rid of the /home.backup directory if you want to. Let me know how it goes. :)

---

### Post by Cowzor on 2008-10-28
Great :) I'll be trying this in a little bit. On another related note, when using the ubuntu installer partitioner, and I choose to mount /var/www and /var/lib/mysql on different disks/partitions, will everything else in /var go onto the disk mounted in / (root)?

---

### Post by caljohnsmith on 2008-10-28
> **Cowzor said:**
> Great :) I'll be trying this in a little bit. On another related note, when using the ubuntu installer partitioner, and I choose to mount /var/www and /var/lib/mysql on different disks/partitions, will everything else in /var go onto the disk mounted in / (root)?
I would assume so, but I've never broken up my main install into that many other partitions, so I can't say for sure. Since you're doing a new install, it certainly won't hurt to just try it and see if it works OK. :)

---

### Post by Cowzor on 2008-10-28
to be honest, neither have I, but I'm still messing around before I'm going to do a serious install anyway :)

---

### Post by Cowzor on 2008-10-28
What you showed me earlier didn't give any errors, but my actual user folder is still in /home.backup and not in /home. Additionally, after rebooting to see if that solved anything (no idea why I thought that), lost+found shows up in /home

---

### Post by caljohnsmith on 2008-10-28
> **Cowzor said:**
> What you showed me earlier didn't give any errors, but my actual user folder is still in /home.backup and not in /home. Additionally, after rebooting to see if that solved anything (no idea why I thought that), lost+found shows up in /home
OK, you'll have see where something went wrong; how about:
```
mount
```
And does that show your home partition is mounted on /home? If it does, and the /home folder is empty, then something must have gone wrong with copying the files over. If the home partition is not mounted on /home, then there's probably something wrong with the /etc/fstab entry for mounting the home partition. What is the partition by the way, in terms of sdX? If you can give more info I can probably help you get through all the steps.

---

### Post by Cowzor on 2008-10-28
> **caljohnsmith said:**
> OK, you'll have see where something went wrong; how about:
```
mount
```
And does that show your home partition is mounted on /home? If it does, and the /home folder is empty, then something must have gone wrong with copying the files over. If the home partition is not mounted on /home, then there's probably something wrong with the /etc/fstab entry for mounting the home partition. What is the partition by the way, in terms of sdX? If you can give more info I can probably help you get through all the steps.

it shows /home is on the right partition. The drive is sdd, partition is sdd1 and there are no other partitions on the drive, if that makes a difference.

---

### Post by caljohnsmith on 2008-10-28
I apologize, I just found my mistake in my previous post and corrected it; I forgot the mount command before you did the copy, so probably your /media/sdb1 folder has all your home files. So run "mount" again and confirm that sdd1 is indeed mounted on /home, and then do:
```
sudo cp -a /home.backup/* /home/.
```
And that should be all it takes to copy your home folder over. Next do:
```
ls -l /media/sdd1
```
And if that directory has all your home files (which is what we would expect), you can delete them with:
```
sudo rm -fr /media/sdd1/*
```
Again, sorry I didn't catch that mistake before, as I thought I went over the steps carefully enough to avoid that, but obviously not. Anyway, let me know how it goes. :)

---

### Post by Cowzor on 2008-10-28
> **caljohnsmith said:**
> I apologize, I just found my mistake in my previous post and corrected it; I forgot the mount command before you did the copy, so probably your /media/sdb1 folder has all your home files. So run "mount" again and confirm that sdd1 is indeed mounted on /home, and then do:
```
sudo cp -a /home.backup/* /home/.
```
And that should be all it takes to copy your home folder over. Next do:
```
ls -l /media/sdd1
```
And if that directory has all your home files (which is what we would expect), you can delete them with:
```
sudo rm -fr /media/sdd1/*
```
Again, sorry I didn't catch that mistake before, as I thought I went over the steps carefully enough to avoid that, but obviously not. Anyway, let me know how it goes. :)

It worked :D Actually, I did ```
sudo cp -a /home.backup/* /home/.
``` just before I read this. Anyway, thanks for all your help and patience :)

---

### Post by caljohnsmith on 2008-10-28
That's great, glad you figured it out. In case you don't want all your home files also in /media/sdd1 though, you might want to delete those at some point. Anyway, cheers and have fun with your new webserver. :)

---

