---
title: "Resize/Shrink/Move Partition without data loss"
date: 2015-07-08
forum: Hardware
---

### Post by newb2 on 2015-07-08
Hello Forum,

I bought a laptop more than a year ago for College, it came with windows 8 pre-installed. Later at some point I wanted to try out Ubuntu, so I shrunk the Data Partition from windows and put Ubuntu on it.
Now a year later, I barely ever use windows and it has the most space. When I open GParted and want to move a partition, it says that it may cause data loss (which I definitely do NOT want).  There are 4 NTFS partitions (recovery, OS, data, restore) and others from the Ubuntu installation (boot, msftres, home, swap, ..). (Don't know why so many...) The problem is that the DATA partition (which I want to shrink) from Windows is not next to the home partition (which I want to grow). Is there a way to go about this without data loss? I'm thankful for all answers!

---

### Post by TheFu on 2015-07-08
Please post the output from 
$ sudo parted -l
and
$ lsblk

---

### Post by weatherman2 on 2015-07-08
First of all, BACKUP YOUR DATA.  You should be doing this anyway for important files even if you don't resize anything; otherwise, you are taking a foolish risk with your data.

And realize you'll need to resize any booted partitions (your Ubuntu partitions) from a live USB boot with Gparted (probably Ubuntu).

No matter what you do with partitions, no matter how trivial, there's ALWAYS a very small risk of something going wrong and you mess up your partition table or your whole hard drive.   (Sometimes it is human error.)  Take the next step  beyond file backup and backup your entire hard drive.  If you have a portable/external hard drive (recommended), you can do this easily with Clonezilla, booted from a live USB.  Clonezilla not only clones from one drive to another, it can make backups of whole hard drives as "images."   (a big directory, actually, with compressed versions of each partition).  So it doesn't need an entire hard drive.  If your laptop has say a 500GB hard drive and you have a 1TB backup drive without enough free space, you can use only part of the 1TB drive for a Clonezilla backup image of the 500GB drive.

Once you've got the backup, then you can do more radical surgery without worrying about messing anything up, because you can always "undo" by restoring your backup.  You could even wipe Windows entirely and use the whole hard drive for Ubuntu.  From your Clonezilla backup, you can restore just your Ubuntu partition(s), fix up your swap etc., update Grub, and you should be good.  Yes, there are a few more steps, but you can basically do it all with a live Clonezilla boot + a live Ubuntu boot (for Gparted - you could boot something else to get Gparted as well).

If you don't have a way to do a Clonezilla backup?  You still need to backup your important files, so even if the partition changes go wrong you aren't out of luck.  As long as you are careful, the risk with Gparted is very low - I've done dozens of resizes, but I would never do an important one without a backup.  Still, keep this in mind: growing a partition from the end forward is easy - usually a 10 second operation.  Growing a partition backward from the beginning of the partition is hard: it basically means moving the entire partition forward, a time-consuming operation (and once you start it, you can't stop it without serious risk of data loss).  So based on your exact partition scheme, that's the trouble you're going to run into.  Sometimes it is just easier to copy the whole partition off with a live USB (e.g. with Clonezilla), then erase/resize other partitions, then copy them back to a new location.

Please post the output of the command

```
sudo parted -l
```

to give an idea of your exact partition scheme, so we can get you specific recommendations based on your exact partition scheme.

---

### Post by newb2 on 2015-07-09
this is the output to parted -l

EDIT: added more to parted -l output and put in code brackets [/edit]

```
Model: ATA TOSHIBA MQ01ABD0 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  106MB   105MB   fat32           EFI system partition          boot
 2      106MB   1050MB  944MB   ntfs            Basic data partition          hidden, diag
 3      1050MB  1184MB  134MB                   Microsoft reserved partition  msftres
 4      1184MB  165GB   164GB   ntfs            Basic data partition          msftdata
 7      165GB   215GB   50,0GB  ext4
 8      215GB   285GB   70,0GB  ext4
 9      285GB   301GB   16,0GB  linux-swap(v1)
10      301GB   301GB   5243kB                                                bios_grub
 5      301GB   729GB   427GB   ntfs            Basic data partition          msftdata
 6      729GB   750GB   21,5GB  ntfs            Basic data partition          hidden, diag


```

hmm ok sounds like a big job, problem is that all the external drives that I do have, don't have enough room :/ 

maybe I need to buy a new external HDD

---

### Post by newb2 on 2015-07-09
oh and thanks for the replies!

---

### Post by TheFu on 2015-07-09
Please edit the **parted** reply and use "code tags" so things line up clearly.
Also - the complete output would be helpful - it has some information I'd like to confirm - no guess.

Lastly - which partition do you want to shrink? There are 2 large NTFS partitions - so it isn't clear.

---

### Post by weatherman2 on 2015-07-09
An easy way to add 16GB to partition #8 (70GB EXT4 partition): delete your swap partition and move it somewhere else.  Then you can grow #8 forward by 16GB - a fast operation.

You'd probably shrink Windows/NTFS partition #5 by that much to make room for a new swap partition.  That should be fairly fast, too - a minute or two, not hours, because you aren't moving it, just shrinking it from the end.

The tricky thing for you will probably be using the new swap partition.  You'll probably need to edit your /etc/fstab file and change the UUID (blkid) of the swap partition to the new one, after you've changed everything.  Use the "sudo blkid" command to get the UUID of each partition after all partition changes are done.  Then replace the swap's old UUID with the new one (it will change when you make a new swap partition). Or if your swap isn't referenced by UUID in the fstab file, change it to the new device ID (/dev/sda5 or whatever).

You don't necessarily need a 16GB swap partition, anyway, if you have a lot of RAM.  4GB is probably plenty.  The ONLY reason you'd want such a huge swap is if you ever want to use hibernation (instead of suspend), and if so, you need a swap partition at least as big as the amount of RAM you have.  If you'll never hibernate, you don't have to worry about the size.

---

### Post by newb2 on 2015-07-10
```
# / was on /dev/sda7 during installation
UUID=0b4e9eb4-f797-41fa-8f63-7a90f36a81dc /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=820b3383-2730-4095-8797-41dff6ca58b7 /home           ext4    defaults        0       2
# swap was on /dev/sda9 during installation
UUID=3e0b25c2-0483-474e-801e-e325ded02d07 none            swap    sw              0       0
UUID=7CC1-F0B4  /boot/efi       vfat    defaults        0       1
```

that is my fstab file currently without the comments on top, what would I need to change?

and ok I will edit the parted post :)

---

### Post by weatherman2 on 2015-07-10
If you are following my suggestion in regards to shrinking the swap / re-allocating that 16GB of space to your ext4 partition, then you would change the line:

```

UUID=3e0b25c2-0483-474e-801e-e325ded02d07 none            swap    sw              0       0

```

by replacing the UUID "3e0b25c2-0483-474e-801e-e325ded02d07" to whatever the new UUID is of the new swap partition you create.  You can find this out using the command "sudo blkid" .

---

### Post by TheFu on 2015-07-10
Be certain to check that the other UUIDs don't change - I think resizing does that.  BTW - resize2fs can grow file systems when online under some situations. I know it works with LVs.

---

### Post by newb2 on 2015-07-11
@weatherman2 : your suggestions sounds simple, problem is that I want  like 100gb from the mtfsdata partition, 16gb wouldn&#8217;t even be worth it  for me :/ 

@TheFu : so if I resize one partition, all other UUIDs  can change? and the OS (or gparted) doesn't update the UUIDs  automatically?

---

### Post by TheFu on 2015-07-11
Yes, the UUIDs are updated automatically, but the /etc/fstab is NOT.
Only the partitions that are modified might change UUIDs. Resizing is a change.  Also, I'm not 100% on that, but if you do resize and reboot and the UUID has changed, then it is likely the partitions that you had before will not be automatically mounted.  This could be a minor inconvenience or the system could refuse to boot - just depends on which partition UUIDs changed.

In short - BEST TO CHECK IT - before rebooting.

sudo blkid
and check the /etc/fstab

---

### Post by weatherman2 on 2015-07-11
The UUIDs probably won't change unless you are moving the partitions forward - then any partition you moved forward may have a new UUID.  Still, you will probably be doing this with a live USB boot anyway, so if you mess up the UUID in your /etc/fstab after you boot, easy to reboot back into the live USB and fix it.  I guess if you are growing partition partition 8 (/home) you might away with resizing from your booted Ubuntu installation - but I'd prefer to do it from a live USB boot anyway.

Here's how I'd probably do it:

1.  make SURE Windows is truly shut down and "fast startup" is disabled:

[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)

2. Backup your important files at least, even if you can't backup everything on the drive.

3. Boot a live USB of Ubuntu or something with gparted on it.

4. sudo blkid > /tmp/oldblkids

5. Make sure all partitions you are planning to resize are unmounted.

6. shrink partition 4 / ntfsdata as much as you want to.  Probably a quick operation.  (Next time you boot back into Windows, this will trigger an automatic chkdsk so be prepared for that.)

7. Move partition 7 (ext4) forward to fill up the free space.  This could be very time-consuming.

8. (Optional) grow partition 7 as much as you want to out of the free space (should be a quick operation).

9. Move partition 8 (ext4) forward to fill up the free space.  Again - could be very time-consuming.

10. Grow partition 8 to use up the new free space (should be quick)

11. Re-do the swap - optional, but as I described earlier, 16GB is probably too big anyway.  You could gain an extra 12GB just by making this a 4GB swap instead of a 16GB swap.  Don't do this if you ever want to hibernate.

12. sudo blkid > /tmp/newblkids

13. sudo diff /tmp/oldblkids /tmp/newblkids

14. If any UUIDs are now different in step 13, mount partition 7 and fix them in your /etc/fstab .

---

The riskiest steps are #7 and #9 - moving the partitions.  Don't interrupt them, even if they take hours.  Be prepared for a long wait.

FYI, Gparted will let you queue up all of these operations and then run them all.  If I had a Clonezilla backup of everything, perhaps that's how I'd do it: launch it overnight, go to bed, hope it's done the next morning.  But you might be more careful and "Apply" each Gparted operation one at a time.  That way, if you made any mistake, you'll know pretty quickly.

---

### Post by TheFu on 2015-07-11
Nice instructions Weatherman - this is one of those times when a little video really would show how easy doing this stuff is.  All the steps makes it seem harder and less intuitive than it really is. 

BTW - next time you install, might be useful to think about using LVM.  Operations like this become much easier and fewer partitions are needed. Of course, LVM is a little more complex, but once you figure it out, whoa - you'll never go back!

---

