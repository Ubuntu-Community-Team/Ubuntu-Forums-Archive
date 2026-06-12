---
title: "[SOLVED] Reinstallation - can I keep my files?"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by tsaotablem on 2008-12-17
So I waited until now to upgrade to Intrepid, and it's gone horribly wrong.

I've been fumbling around with it since last night.  I got a number of errors that I worked through, including the root partition being read-only and the Gnome Settings Manager failing to start.  Now I'm at my wits end as my machine won't boot (kernel panic).  I just downloaded the live .iso and I'm tempted to just reinstall.

My noobi question is: if I reinstall from the CD, will I lose my data?  Is there a particular method I should follow for when I do the install?

Please keep in mind I'm quite a noob and don't know what I'm doing, so I'm sorry if this is a really dumb question.

Thanks.

---

### Post by taurus on 2008-12-17
Do you have a separate /home partition or do you only have two partitions on your harddrive: / & swap?

From the LiveCD, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by tsaotablem on 2008-12-17
Thanks for the quick response.
Here's what I got:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 30.8 GB, 30839584768 bytes
255 heads, 63 sectors/track, 3749 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xda1ea924

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3656    29366788+  83  Linux
/dev/sda2            3657        3749      747022+   5  Extended
/dev/sda5            3657        3749      746991   82  Linux swap / Solaris

Disk /dev/sdb: 10.2 GB, 10239860736 bytes
255 heads, 63 sectors/track, 1244 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x21372d3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1244     9992398+   c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by taurus on 2008-12-17
Looks like you only have one big partition for Ubuntu (and a swap partition).  Therefore, if you have valuable files that you need to backup, do it before you reinstall since you want to reformat your partition, /dev/sda1, when you reinstall so you would have a clean new install.

I guess you can back up your files from /dev/sda1 to /dev/sdb1 unless /dev/sdb1 is running low on space.

```
sudo mkdir /media/ubuntu /media/backup
sudo mount -t ext3 /dev/sda1 /media/ubuntu
sudo mount -t vfat /dev/sdb1 /media/backup -o umask=000
df -h
```
You can now access your $HOME directory on the harddrive through /media/ubuntu--/media/ubuntu/home/**username**.

Replace **username** with your actual login name.

And your 10GB drive is mounted to /media/backup.

```
ls -la /media/backup
```

---

### Post by tsaotablem on 2008-12-17
Thanks for that info.. I am able to view and modify the files on the partition that won't boot on its own.. but you correctly guessed that 10GB isn't enough for me to back my files up onto.  I am trying to share the directory to be backed up on my network but the Samba install from the Live CD is failing (it's complaining about perl).
If I can get Samba fired up and get the files to another rig on my network then I'll be more than happy to blow away this partition and do a fresh install.
The alternative would be to recover from this kernel panic error.  I have no idea how to do that.. anyone have any thoughts??

---

### Post by taurus on 2008-12-17
How did you install samba from the LiveCD?

---

### Post by tsaotablem on 2008-12-17
Actually got it to work.. copying my files over as we speak.
I right-clicked on the folder to share, selected the share tab, selected the 'share' toggle.  Update Mgr advised that some files would need to be installed, I said go ahead.  As mentioned, the first time I tried it just whined about perl and hung on me, but I tried again after a reboot and some messing around and it worked.  So it looks like once my files are safe I'll just do the full, fresh installation.  I'm just disappointed the upgrade method didn't work.  I thought I was being clever by waiting for the initial rush to subside.  :)

---

