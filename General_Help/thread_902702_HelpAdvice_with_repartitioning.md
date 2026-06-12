---
title: "Help/Advice with repartitioning"
date: 2008-08-27
forum: General Help
---

### Post by Znupi on 2008-08-27
Using Ubuntu 8.04 if that makes any difference.

Here's my partition setup:
[IMG]http://i80.photobucket.com/albums/j161/znupi/ubuntu/GParted.png[/IMG]
Let me explain:
**/dev/sda1** is where Windows used to be. All there is now is a Windows virtual disk (for a virtual machine) which can be easily moved to another partition.
**/dev/sda5** is my "media" partition.. it holds movies, cartoons, music, etc.
**/dev/sda6** is my root ubuntu partition.

My questions:
**1)** What's /dev/sda2 ?? What does 'extended' mean and what does the fact that the other partitions are children of /dev/sda2 mean?
**2)** I feel like my root partition is getting low on disk space (btw, why is gparted reporting 5.5GB free space while nautilus reports only 4.5GB?). Since I recently removed Windows, I'd like to resize /dev/sda1 to 15GB and mount it as /home, and give the other 5GB to /. The way I see myself doing this: shrink /dev/sda1 and format, move /dev/sda5 5GB back, expand /. This brings a few questions:
a) Is this doable? Would I totally screw my system up?
b) Would my system still boot? The /dev/sda1 has the "boot" flag. What happens if I format it?
c) Is there any way besides running a LiveCD in which I can manage (expand) my root partition? Right now I can't see how because I can't unmount it.

Thanks :)

---

### Post by arch0njw on 2008-08-27
1) Try this for an explanation of the partitions:  [http://en.wikipedia.org/wiki/Disk_partitioning#Primary_.28or_logical.29](http://en.wikipedia.org/wiki/Disk_partitioning#Primary_.28or_logical.29)  It seems to mostly come down to how the master boot record can deal with things.  I'm sure there is a much more hardware technical explanation about it, but Wiki answers this to my level of understanding.

2) Your root partition could probably benefit from some housekeeping.  For example "sudo apt-get clean" ("man apt-get" to learn more about it).  IMO, 10GiB is probably quite small if you are going to have a lot of big files.  For example, ASUS Eee PC can be bought with a 12GiB drive, and that obviously assumes the persion isn't going to be keeping a multimedia library on it...

Also, do you have several kernels installed?  That can take up space.  I tend to keep only one version back and remove the rest.

To work around this kind of situation, I have sometimes created symbolic links to larger partitions when I didn't want to mess with resizing partitions.  So I would move all my big files (picture, music, etc.) elsehwere, and create sym links to them (e.g.:  cd ~; ln -s /path/to/new/dir/for/music Music)

Maybe someone else could clarify why gparted and Nautilus are reporting different numbers.  I'm not sure why.

I think if I were faced with this partitioning situation, I would backup and repartition the way I want things.  You could probably juggle this, but (1) you would definitely need to do it from a Live CD, and (2) any time you juggle the partitions you should backup.  You need to do this from a Live CD because you can't toy with mounted partitions.  That's a bit like working on your car while going 100MPH down the highway...

I also suggest that if you do this, reformat sda1 to ext3 (or some other, better format) unless you really need it to be readable by Windows.

There is a great GParted Live CD to help with this sort of thing.
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

---

### Post by prshah on 2008-08-27
> **Znupi said:**
> 
[IMG]http://i80.photobucket.com/albums/j161/znupi/ubuntu/GParted.png[/IMG]
**1)** What's /dev/sda2 ?? What does 'extended' mean and what does the fact that the other partitions are children of /dev/sda2 mean?

A hard disk can have a total of 4 partitions; This can be any combination of extended or primary partitions. Extended partitions are a way to allow more than 4 partitions on a hard drive. So you can have 3 primary partitions, and then any number of (as you put it) "child partitions" on a single extended partition. These "child" partitions are actually called "logical drives" (Though they are obviously not drives; go figure).

> **Znupi said:**
> 
**2)** I feel like my root partition is getting low on disk space (btw, why is gparted reporting 5.5GB free space while nautilus reports only 4.5GB?).

10Gb is OK for a regular ubuntu installation, but if you're going to add a lot of programs to the mix, it's not much. Some portion of the space is reserved for "root" (superuser) only access, this is to prevent an full hdd from bringing the system down. There's always a little "wiggle" room which only root user can use, and then he can clear a little space for other users.

> **Znupi said:**
> 
Since I recently removed Windows, I'd like to resize /dev/sda1 to 15GB and mount it as /home, and give the other 5GB to /. The way I see myself doing this: shrink /dev/sda1 and format, move /dev/sda5 5GB back, expand . This brings a few questions:
a) Is this doable? Would I totally screw my system up?
b) Would my system still boot? The /dev/sda1 has the "boot" flag. What happens if I format it?
c) Is there any way besides running a LiveCD in which I can manage (expand) my root partition? Right now I can't see how because I can't unmount it.


Yes, it's do-able, but will need a lot of extra activity, depending on your current setup; I _think_ at a minimum you will lose and will have to re-install grub. The "boot" flag can be put back using fdisk from the live CD, but I don't see the sense in make a "/home" partition as bootable, and you cannot make extended partitions bootable... this is getting confusing. What is your current setup? Grub installed to MBR or particular partition?

In any case, if you're creating a separate "/home", you don't need the additional 5Gb space for "/"; I've installed Ubuntu, with kubuntu-desktop and xubuntu-desktop with a "/" of 10Gb, with a separate "/home". You will also have to study specific guides on how to move your existing "/home" to the new partition. (Just copy/pasting the files from the live CD will not do.)

Lastly, you're right about using the boot/live CD to handle "/" partition resizing; there is no other way.

All considered, I'd suggest a nice, clean new install with sanity in partitioning :)

---

### Post by Znupi on 2008-08-27
Thanks to both of you for the explanations! Really helpful!
By now knowing that only primary drives can boot, it is clear to me that "/" must be installed to such a partition. Thus, I've come up with a new plan: reinstall Ubuntu to /dev/sda1 (20Gb should be enough for Ubuntu right?), delete /dev/sda6 and expand /dev/sda5 by 10GB. I think it's a lot more doable and less dangerous.

**arch0njw:** apt-get clean freed a whole GB! Wow! Thanks! Why doesn't Ubuntu run that command regurarily? About sym links: I don't like having music in my /home directory (neither on Windows did I keep music in My Documents), so that's not the problem.
[quote=prshah]Grub installed to MBR or particular partition?[/quote]
Absolutely no idea :)

Thanks again for your excellent answers!

---

### Post by prshah on 2008-08-28
> **Znupi said:**
>  Thus, I've come up with a new plan: reinstall Ubuntu to /dev/sda1, delete /dev/sda6 and expand /dev/sda5 by 10GB. I think it's a lot more doable and less dangerous.

apt-get clean freed a whole GB! 

Yes, that seems to be a good idea. But if you are planning for a whole fresh re-install anyway, here's a better partitioning scheme (Assuming you don't want Windows)

[FONT="Courier New"]/dev/sda1 (Primary Partition 1), Mount point "/", ext3 - 10 Gb (or 15Gb for paranoia)
/dev/sda2 (Primary Partition 2) , Mount point "", swap - 1.1 Gb ( Or 1.1 x RAM)
/dev/sda3 (Primary Partition 3), Mount point "/home", ext3 - Everything else.
[/FONT]
Advantages: 
a) Cleaner partitioning
b) If in the future you decide to re install windows, you can just shrink the "/home" partition, create an extended partition and logical drive (from linux), format the logical drive (from Windows installer) and install away.

apt-get clean removes the .deb files downloaded by update-manager and apt-get commands. These files are not required once installed. I agree it's a good idea for it to be cleared periodically, and I have setup a cron job to do just that, once a month.

---

### Post by Znupi on 2008-08-28
**prshah:** I can't do that, because I'd have to format /dev/sda5 (well, remove it actually) and I don't want to lose all my media. And I don't feel like backing up 70GB. I'd need like, what? 20 DVDs? Also, I only use /home for pics and docs, so it's ok if I don't create a separate partition for it.
Thanks for your advice. I admit that your setup is MUCH cleaner and I wish there was some way to achieve it. Maybe when I get a blu-ray writer ;)

---

### Post by prshah on 2008-08-28
> **Znupi said:**
> 
and I don't want to lose all my media. And I don't feel like backing up 70GB. 

Yes, I overlooked that bit; well, anyway.

btw, you should be aware that copying/moving involves a "bit" of risk if the operation is interrupted. Some people in the forums have reported that resizing/moving takes a long time; anything from hours to 2 days (!!).

However, I have never had a problem; all of  my operations (including moving a 60Gig partition) have completed in under 45 mins; 20 mins is the norm. And though it is supposed to be fraught with danger, it has become so commonplace for me that I don't even bother with the recommended backup. I hope your mileage doesn't vary ;)

In fact, here's yet another idea for you to consider; delete the extra partitions in the extended partition, reduce the size and simulatneously move the entire partition to the end of the disk (gparted can handle that in a very simple way, not to worry); then follow the scheme as above. While I understand you not wanting a separate "/home", it can definitely alleviate future potential problems.

Note however that resize/moving risks still apply.

Good luck with whatever you decide!

---

### Post by Znupi on 2008-08-28
I know resize/moving operations can be dangerous, that's why I chose to reformat /dev/sda1 to ext3 and install Ubuntu there. The only 'risky' operation will be expanding /dev/sda5 by another 10GB. Although I've resized this partition a few times in the past and everything went fine. I hope I don't run into any problems with it. Thanks again for your advice :)

---

