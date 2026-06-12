---
title: "Move Ubuntu installation to a new drive"
date: 2006-09-13
forum: Hardware &amp; Laptops
---

### Post by ate50eggs on 2006-09-13
I am dual booting to Ubuntu and XP. Right now I have a a 60Gb HD that is starting to show some wear and tear. Basically it's too small and, although it hasn't actually failed, I don't totally trust it. What is the smart way to move my Linux installation to this new drive so that my drivers, configuration files, etc work right?

Is there a benefit to installing from scratch? and if so are there a few key files I can just move over?

---

### Post by Sarisar on 2006-09-14
I'm still trying to sort out a complete list, but basically you need most thigs in your home directory (including hidden files!).

For example if you use evolution there is a .evolution folder in your home directory that has your emails (but not your account details strangely enough).

The easiest way may be to put the new HD in as primary and have your current one as secondary and copy files over.  Although I've not tried that so not sure how that would exactly work (can someone else confirm if that is OK?)

---

### Post by yota on 2006-09-14
Hi,

It can be done: I'm writing from an installation that not only had been through 4 different drives but on 4 different computers too! 
I really love linux "features" like this: you only reinstall if you like to...

The concepts are simple, but is quite easy to forget something and end up with a machine that doesn't want to boot (everything can be repaired later anyway).

Let's try to give some hints.

-Method 1: backup with tar a system while it's running.

I won't enter in details, suffice to say that you can make a tarball of all your system with something like
```

tar -psScvzf - --exclude='/media/*' --exclude='/proc/*' --exclude='/sys/*' --ignore-failed-read /  | split - -b 4000m /media/Removable/backup.tar.gz

```
and then explode it to your new drive.

```

cat /media/Removable/backup.tar.* |tar -xz -D <path_to_your_new_drive(already_formated_and_mounted)>

``` 

Plus: 
-you can do it while you're working
-good backup method
Minus:
-compression time is useless if migration is the only need
-while the system is running rarely something can be lost (locked files etc.)
-additional space is required to store backup

-Method 2: Boot with live cd and copy everything

From a live cd mount your new drive, let's say in /mnt/new and your old one in /mnt/old, then simply
```

sudo cp -va /mnt/old /mnt/new

```

Plus:
-faster
-100% reliable
-no extra unit/space is needed
Minus:
-the computer is occupied during the operation
-live cd is needed

-FINISH IT (common to both methods)
Something remains to be done:
[LIST]
[*]Restrore grub in the boot sector (always needed)
[*]correct /etc/fstab (if partition scheme on new drive is different than before)
[*]correct /boot/grub/menu.lst (if partition scheme on new drive is different than before)
[/LIST]
If you need help on these items ask specifically!

Nice migration!
:)

---

### Post by MichaelLehner on 2006-09-14
The way i would chosen is to use the dd function of linux. You can use it to copy anything to any other location. But you should use it with care, because you also could damage the system this way.

How to copy the system if you also want to move the windows system to another harddisk, you need a disk which has the same size or greater than the disk you want to change. Connect both drives to your system and boot from live-cd, if it also works when you boot your system, i don't know. Now you can copy the whole disk using this:

```
dd bs=1M if=/dev/[Source disk] of=/dev/[destination disk]
```

For example:
```
dd bs=1M if=/dev/hda of=/dev/hdb
```

When ready, you could change partition sizes of the new disk, if it was greater than the old one. If you plug it in the same way, the old one was, you should be able to boot again. I used this to save my os, because a disk was crashing. This was a Windows-disk, but i think if it works with windows it would also with linux and you wont loose anything if it doesn't.


If you want XP stay on the old disk, there would be more to do, because you only can copy single partitions. But there is also a way to get a working installation without installing anything. First i would create the same partitions than on the old drive (only the ones you want to move). now you could use the same commands to copy the information. But the source and destination isn't the whole disk, but only the partitions. I don't know your diskconfiguration, i'll use this one:
[INDENT]
hda1   /boot
hda2   /
hda3   XP[/INDENT]


```
dd bs=1M if=/dev/hda1 of=/dev/hdb1
dd bs=1M if=/dev/hda2 of=/dev/hdb2
```

The next step would be to fix the mbr to find the bootloader, this depends on how you put in the two disks, it would be best if you figure this out for yourself or tell me a little more about your configuration.

The last step should be to fix your /etc/fstab file, if the device names for your mount points have changed. You would have to do very much by yourself, but i think you will be faster than installing the whole system and everything you changed after that.

Good luck
Michi

---

### Post by ate50eggs on 2006-09-14
Thanks for your help. I'm still a little unclear on what to do about the partitions. Do I format and partition the new disk first? How do I adjust them afterwards to make everything work out right?

I've heard it's possible to make an image of a partition and just copy it over. Which method is that?

Also some info I should have given before - I will be re-installing windows from scratch, but I am going to get some data files off of that partition. I plan to transfer files by mounting both drives simultaneously (though I'll probably pitch the old one afterwards).

right now the live CD method seem most sensible to me. Oh, and I'm not sure what to do about grub. I haven't played with it before.

 Thanks again

---

### Post by MichaelLehner on 2006-09-14
what would you do with the old disk after moving the system to the new one? If you want move all to the new one, i would choose my first way, everything will work after unpluging the old disk and putting the new one on the same position. after that you could reinstall your windows, but this will then break your grub, if you install on the same disk, because windows always rewrites the mbr, after the installation you will have to boot frome a live-CD with grub and perform about 4 to 6 commands (i'll have look for), to get grub work again. But this isn't realy a problem.

By using this method you wont have to do anything with your new disk. just get it out of the box, plug it into the computer, boot from live-CD and perform the dd command i wrote in my last post. But check 3-times to insert the right devices for source and destination, because for example mixing up source an destination would write the new garbage from the new disk over the data you need of the old one. but if you make everything right, you get your data, partition table and even the mbr copied from the old disk to the new one. If the new disk has a greater size there would be unpartitioned space at the end of the disk. You can use this by creating a new partition ore changing the size of the old ones.

When you know how your new configuration looks like and what has changed, feel free to post this, there will be a solution how to fix everything again.

---

### Post by yota on 2006-09-14
> 
Thanks for your help.

You're welcome!
> 
I'm still a little unclear on what to do about the partitions. Do I format and partition the new disk first? How do I adjust them afterwards to make everything work out right?

The method (let's call it 3, ok?) suggested by MichaelLehner has the advantage of raw-copyng everything, partition scheme and filesystems included. So in this case you would have not to partion and format.

With mine suggestions instead you have to partion disk and format filesystems (both things can be done in live cd) before copying.

To reinstall grub
```

grub-install --root-directory=/mnt/new/ /dev/*your-hd-dev*

```
having mounted the new disk on /mnt/new

---

### Post by MichaelLehner on 2006-09-14
but you don't have to reinstall grub itself i think, you only need to rewrite the mbr, pointing to the position of grub (possibly new). if your partitions have changed you also have to change the boot-sequences for the different systems.
If i'm wrong, please tell me, but it worked after a reinstallation of a windows system, which broke grub.

---

### Post by ate50eggs on 2006-09-14
ok, I'll give this a shot as soon as I get home. 

Using the dd method copies over the partitions correct? the new drive is much bigger. Can I make the partitions bigger once they're copied? 

Will the dd method copy all the partions? one partition at a time? linux partitions only? I don't exactly understand how it works.

---

### Post by MichaelLehner on 2006-09-15
dd copies everything to every position you want it to. You also can write the whole disk data to a file. It gets the bytes from if and puts them on/in of. If you execute dd if=/dev/random of=/dev/hda, you will waste all your data in hda. It copys them correct, but it even doesn't know about partitions, but the partition information also is only data on your disk, because of that it also gets copied and is available on the new disk. It also doesn't matter obaut file systems, you could create one by yourself, create a partition with it and copy the disk with dd, it will also be able to copy this type, even if only you know know the spezification. I moved a windows installation by this method and everything i had to do after copy, was to change the disks, because the new one had to be at the position of the old one.

After the copy process you could adjust the partition sizes using GParted (Linux) or Partition Magic (Windows). Partition Magic you now get from Symantec, because they bought PowerQuest. I also had to to this, because i switched from 250GB to 300GB and it worked fine.

---

### Post by jwalker on 2006-09-18
> **MichaelLehner said:**
> The way i would chosen is to use the dd function of linux. You can use it to copy anything to any other location. But you should use it with care, because you also could damage the system this way.

How to copy the system if you also want to move the windows system to another harddisk, you need a disk which has the same size or greater than the disk you want to change. Connect both drives to your system and boot from live-cd, if it also works when you boot your system, i don't know. Now you can copy the whole disk using this:

```
dd bs=1M if=/dev/[Source disk] of=/dev/[destination disk]
```

For example:
```
dd bs=1M if=/dev/hda of=/dev/hdb
```

When ready, you could change partition sizes of the new disk, if it was greater than the old one. If you plug it in the same way, the old one was, you should be able to boot again. I used this to save my os, because a disk was crashing. This was a Windows-disk, but i think if it works with windows it would also with linux and you wont loose anything if it doesn't.


If you want XP stay on the old disk, there would be more to do, because you only can copy single partitions. But there is also a way to get a working installation without installing anything. First i would create the same partitions than on the old drive (only the ones you want to move). now you could use the same commands to copy the information. But the source and destination isn't the whole disk, but only the partitions. I don't know your diskconfiguration, i'll use this one:
[INDENT]
hda1   /boot
hda2   /
hda3   XP[/INDENT]


```
dd bs=1M if=/dev/hda1 of=/dev/hdb1
dd bs=1M if=/dev/hda2 of=/dev/hdb2
```

The next step would be to fix the mbr to find the bootloader, this depends on how you put in the two disks, it would be best if you figure this out for yourself or tell me a little more about your configuration.

The last step should be to fix your /etc/fstab file, if the device names for your mount points have changed. You would have to do very much by yourself, but i think you will be faster than installing the whole system and everything you changed after that.

Good luck
Michi


Hi

Thanks for this, I am the hell n00b and I did exactly what a wanted to do with no problems. So +1, thanks. I would recommend this solution to anybody who just brought a brand new HD that has never been formatted, and simply wanted to make an exact copy of their existing HD. After that swap the HDs and you're away! Thank you! 250>20

Are you able to provide more info about adjusting the paritions after the data transfer? Using QTParted, my paritions appear to be 'locked'. 

Thanks again

Chris

---

### Post by MichaelLehner on 2006-09-18
hi,

i'm sorry, i don't know QTParted. The Problem is my internet connection is a bit to expensive to spend hours on downloading packages, because of that, i wasn't able to change really to linux and only use it, when there is no solution in windows for a problem.

But is it possible that you have mounted the partitions you want to change? This could be the reason why they are locked. I would suggest to boot from a liveCD and use QTParted. But there should be also a solution by changing the partitions while they are mounted, because i read somewhere, that it's locked for less experienced users. but i think using a live CD would be the way which is the secure one. If you don't find a LiveCD with QTParted, try GParted ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) they provide LiveCDs or LiveUSB themselves.

I hope this will help you.

Michi

Edit 14:45: I found out, that in the features section of QTParted is a little list of supported file systems, according to this list, it is only able to read linux file systems and you can't resize them. This could also be a reason why there is a lock on them. But I don't know if this list is complete. GParted has a greater list of supportet filesystems.

---

### Post by jwalker on 2006-09-18
Thanks for your input once again, I will keep at it.

---

### Post by ate50eggs on 2006-09-20
Thanks again for your help. dd works great! I've tried to resize the partitions with Partition magic, but it keeps effing up. As mentioned before, QParted is not useful for disks with ntfs partitions. I have a few ideas on how to get this opperational and I'll post when I have a solution.

---

### Post by ate50eggs on 2006-09-26
OK, this has been pretty frustrating, but I've my box working. As I said dd works great, but adjusting the partitions is a real problem.

eventually I decided to just make a new ntfs partition and leave everything else the same. unfortunately this made my ubuntu installation unuseable. it would load the kernal, but wouldn't start x. so i wound up reinstalling. (I probably could have found a way to fix it, but I was pretty burnt out at that point and I just wanted it to work).

Some things I tried unsucessfully:
- using the 'redistribute free space' function of partition magic
- using partition magic to partition the new drive and then using dd to move a partition at a time. parition magic read the entire disk as 'bad' until I used the partitioner from the ubuntu install disk to put a filesystem on it.

basically partition magic has been a huge pain and does not work as advertized. I will say that my drive is terrifyingly loud and, alough it works right now, I'm not convinced that it isn't a lemon. your mileage may vary.

thanks again for your help

---

