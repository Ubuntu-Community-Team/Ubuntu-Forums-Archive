---
title: "Dual XP and Ubuntu and no space to update?"
date: 2009-07-13
forum: Installation &amp; Upgrades
---

### Post by egruber on 2009-07-13
I just installed Ubuntu on a Thinkpad T60 alongside Microsoft XP.  I let Ubuntu pick the partition sizes.  When I wanted to apply updates I got the following:

[B]Not enough free disk space

The upgrade needs a total of 366M free space on disk '/'. Please free at least an additional 163M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
[/B]
Did I do something wrong?  Can I correct it?

---

### Post by merlinus on 2009-07-13
Post results of

```
df -h
```

Did you use the sliders when at the partitioning screen to set the size of /?

---

### Post by egruber on 2009-07-13
No. I let Ubuntu select the sizes.  I did not touch the slider.

---

### Post by merlinus on 2009-07-13
Therein lies your problem.

Meanwhile, you may be able to grow your / partition.P ost results of

```
sudo fdisk -l
df -h
```and if possible, a screenshot of gparted.

---

### Post by egruber on 2009-07-13
But I did let it import my docs and settings so I have a volume called 'preload'.  I wasn't sure when it asked me, so I said yes.

---

### Post by egruber on 2009-07-13
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.1G  176M  93% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M   92K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  156K 1007M   1% /dev
tmpfs                1007M  472K 1006M   1% /dev/shm
lrm                  1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volat

---

### Post by raymondh on 2009-07-13
> **egruber said:**
> Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5             2.3G  2.1G  176M  93% /
tmpfs                1007M     0 1007M   0% /lib/init/rw
varrun               1007M   92K 1007M   1% /var/run
varlock              1007M     0 1007M   0% /var/lock
udev                 1007M  156K 1007M   1% /dev
tmpfs                1007M  472K 1006M   1% /dev/shm
lrm                  1007M  2.4M 1004M   1% /lib/modules/2.6.28-11-generic/volat

Can you post a screenshot of gparted (to help us visualize) so the forum can recommend/suggest a plan-of-action?

You may have to take some space from XP ... as you can see now with the 93% full.

---

### Post by egruber on 2009-07-13
I attached the screen shot (I hope).

---

### Post by merlinus on 2009-07-13
Given the ntfs preload partition, you do not have much room left.  That is why ubuntu had such a small space for itself.

All things being equal, and since you do not have another OS on this hdd, you will probably be best off starting fresh with a new install.  This time do not import anything.  If you have data that is backed up, you can copy it over later.

If you want suggestions for partitioning, post back.

---

### Post by egruber on 2009-07-13
Can it be done so I have a reasonable amount of space for both XP and Ubuntu?  Or is having both really not a good idea.  I wouldn't mind a 50/50 split.  What do you suggest?

---

### Post by egruber on 2009-07-13
> **merlinus said:**
> Given the ntfs preload partition, you do not have much room left.  That is why ubuntu had such a small space for itself.

All things being equal, and since you do not have another OS on this hdd, you will probably be best off starting fresh with a new install.  This time do not import anything.  If you have data that is backed up, you can copy it over later.

If you want suggestions for partitioning, post back.

Does that mean I just reinsert the DVD and start the install again, leave the sliders alone, but do NOT import the User settings and docs form xp?  So I can still have both?

---

### Post by merlinus on 2009-07-13
Please explain what you mean by, "So I can still have both?"

With a fresh install, you will select use entire disk at the partitioning screen.  My suggestion is to allocate 10G for /, 1.5G for /swap, and use the rest for /home.  YOu may have to manually specify the sizes of these partitions, and deifinitely to format them as ext3 and their mountpoints (/, /swap, /home).

You can do that by rightclicking on the partitions and using the dropdown menus.

Alternatively, you can follow guides such as this:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by egruber on 2009-07-13
I meant whether I can still have XP and Ubuntu boot on the same machine.  If that is feasible, can you suggest how to partition?  Or will Ubuntu make the right choices if I do NOT import the Preload volume.

---

### Post by merlinus on 2009-07-13
Do you have xp on a different hdd?  I did not see it in the gparted screenshot.

---

### Post by egruber on 2009-07-13
No.  It is on the same hard drive.  It boots up fine when selected.

---

### Post by merlinus on 2009-07-13
So sda1 is windows, marked preload?  And what is sda2?

As things stand, you have but the minimal space for ubuntu.  You might try shrinking your windows partition to free up more space.

---

### Post by qamelian on 2009-07-13
> **merlinus said:**
> Do you have xp on a different hdd?  I did not see it in the gparted screenshot.
It appears to be sda1, labelled "preload".

EDIT: Oops! Wasn't quick enough on the draw! :)

---

### Post by egruber on 2009-07-13
What if I just want to delete Ubuntu and return to an XP only HD.  Is there a way to do that?  Or do I have to start over and reinstall XP and wipe out ubuntu in the process?

---

### Post by raymondh on 2009-07-13
> **egruber said:**
> What if I just want to delete Ubuntu and return to an XP only HD.  Is there a way to do that?  Or do I have to start over and reinstall XP and wipe out ubuntu in the process?

You can use XP's disk management tool to delete the ubuntu partition and then expand the windows partition. You can also use gparted (from the liveCD) to do that.  Note, there are 3 ubuntu partitions ... root (/), swap and EXTENDED. 

With Ubuntu gone, you'll need to correct the MBR as it has been overwritten by GRUB.  Boot into the original **XP install disc** (not recover disc) > **R** (for repair) and type **fixmbr**.

[http://support.microsoft.com/kb/314058](http://support.microsoft.com/kb/314058)

Or, alternatively, you can pop in the XP install disc and choose to install and reformat the whole drive.  That will erase all existing data (including Ubuntu).

Or, you can try to shrink XP and expand Ubuntu using gparted from the liveCD.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Back-up your files.  Let the forum know if you want to try to shrink-expand instead.

Good luck.

---

### Post by egruber on 2009-07-13
I'll give it some thought.  Thanks for all your help!

One more question, because I'm just a little unsure at this point.  If I want to share this PC with Ubuntu and XP.  Will I have the same issues if I:

1. Wipe the hard disk and reinstall XP.
2. Install Ubuntu.
    2a. Do I adjust the sliders or leave them alone?
    2b. Assume I do NOT import anything.

Will I then have reasonable space to have both?  Or must I adjust the sliders?  Or just pick ONE OS and let it go.

Then I promise to leave you alone for today!

---

### Post by raymondh on 2009-07-13
> **egruber said:**
> Then I promise to leave you alone for today!

LOL.  No worries :)

You have to use the slider (from choosing GUIDED RESIZE) to dictate how much space you want to give Ubuntu and subsequently, how much space you want to leave for XP.  If not, you will be left with another 2.3GB Ubuntu set-up.

For your reading/reference:

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
[http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm](http://apcmag.com/how_to_dual_boot_windows_xp_and_linux_xp_installed_first.htm)

If you want to dictate partitions (i.e. create the partitions prior to installing hence giving you the flexibility, etc.) ...

[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)
[http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-specify-partition-size-and-location](http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-specify-partition-size-and-location)

You may want to consider separating your /home from root (/) which gives you the advantage of retaining your settings and config files, etc. should you need to re-install/upgrade versions of your ubuntu.  This can be done prior to installiing Ubuntu or even after. 

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

If you wish to resize, shrink and extend:

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Plus, the forum will always be here to help you.

Good luck.

---

### Post by egruber on 2009-07-14
Thanks for passing these along.  I guess what threw me was that Ubuntu by default picked such a small partition. The documents you sent were from the Hardy Version and the illustrations show the default partition for Ubuntu to be larger than XP (as much as 70%) and they recommend reducing it with the slider. With Jaunty I left it alone and got a very small space for Ubuntu.  Did they change the default for the new release?  Or did I miss something?

---

