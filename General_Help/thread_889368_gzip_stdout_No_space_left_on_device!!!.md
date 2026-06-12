---
title: "gzip: stdout: No space left on device?!?!?!?"
date: 2008-08-14
forum: General Help
---

### Post by morbid_bean on 2008-08-14
After having former issues with my past ubuntu install i wipe it out and reinstalled a fresh one....here i am all excited and everything when suddenly i get this....

```
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```

when i try to do some extra updates

go to terminal and i type "sudo dpkg --configure -a"

i get..

```
sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic

gzip: stdout: No space left on device
update-initramfs: failed for /boot/initrd.img-2.6.24-19-generic
dpkg: subprocess post-installation script returned error exit status 1

```

so alredy getting problems....

---

### Post by sdennie on 2008-08-14
What is the output of:

```

df

```

---

### Post by morbid_bean on 2008-08-14
> **vor said:**
> What is the output of:

```

df

```

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda4             19938868   2404420  16529584  13% /
varrun                  192764       104    192660   1% /var/run
varlock                 192764         0    192764   0% /var/lock
udev                    192764        68    192696   1% /dev
devshm                  192764        12    192752   1% /dev/shm
lrm                     192764     39760    153004  21% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3                46665     41295      2961  94% /boot
gvfs-fuse-daemon      19938868   2404420  16529584  13% /home/jimbo/.gvfs
/dev/scd0               715898    715898         0 100% /media/cdrom0

```

---

### Post by sdennie on 2008-08-14
I'm not sure why you made a /boot partition and made it so small but, that is the source of your problems: The kernel is trying to install into a tiny partition and there is no room left.  You will probably need to repartition, drop the /boot partition and play some grub/fstab trickery or, if it's a new install, just reinstall and let /boot live on the same partition as /.

---

### Post by morbid_bean on 2008-08-14
> **vor said:**
> I'm not sure why you made a /boot partition and made it so small but, that is the source of your problems: The kernel is trying to install into a tiny partition and there is no room left.  You will probably need to repartition, drop the /boot partition and play some grub/fstab trickery or, if it's a new install, just reinstall and let /boot live on the same partition as /.

ahh ok because I decided to try this guide i found it said

"The other one is a small ext3 partition (put it 50Megs) and mount it to /boot (Very important to do that!!)"

[http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/](http://digitalgraphy.wordpress.com/2007/10/20/dual-booting-ubuntu-and-windows-ntxpvista/)

so just have a swap and ext3 partition i take it??

and aside this post is 512mb good for swap?

---

### Post by sdennie on 2008-08-14
50M is woefully inadequate for /boot and I'm slightly surprised the installer even let you make a /boot that small (it sounds like a bug).  If you really want a /boot partition, 500M is probably sufficient but, if you are short on disk space, I just wouldn't bother to make a /boot partition and let it live on the / partition.

I personally create a / and /home partition and give ~10G to / and the rest to /home.  That way you can cleanly re-install without having to upgrade and you keep your personal information/settings.

Also, 512M of swap is probably fine unless you run a laptop and want to use the hibernation feature.  In which case, you'd want to have at least as much swap as you have physical memory.

---

### Post by morbid_bean on 2008-08-14
what is the /boot for is it really necessary?

---

### Post by sdennie on 2008-08-14
It's generally not necessary.  There may be other examples but, if, for example, you ran a RAID array or LVM for /, you'd need a /boot as something like ext2/3 to get the system to the point where it could load the drivers to mount your "exotic" / partition because asking a simplistic and purposely lean bootloader like grub to understand a billion filesystem types and configurations is simply not plausible.

---

### Post by klompen on 2008-08-18
I've got the same situation - my /boot is just about the same size and usage as Morbid_bean's, but is on /dev/md0. My server is set up as a software raid with 2 500gb drives.  Is there some kind of disk partitioning utility that can move the partitions to create room for enlarging /boot? I'm fairly new to Ubuntu and although I managed to get the software raid set up I'm really unsure about trying to recreate some of what I have working (like a Samba share).

---

### Post by cariboo on 2008-08-18
You've done the hard part already :) getting the raid to work, everything else should be fairly easy. I'm not sure if gparted will work on a raid array, but if you want to try it, you'll have to use the LiveCD as the drives have to be unmounted to do any partiton work on them.

Jim

---

### Post by fjgaude on 2008-08-18
gparted doesn't know raid. We use cfdisk.

---

### Post by Jamo_Leeds_Aus on 2009-08-15
I have the same small boot partition for a raid set and had the same issue. Instead of RePartitioning everything , I went and deleted duplicates from my boot folder. IE latest versions were 2.6.28-14 so i deleted all 2.6.28-11. This allowed me to run the dpkg --configure -a without error and then use apt-get without issue. I know this is a late post but hopefully it may help someone.

---

### Post by adamtog on 2009-11-28
Jamo_Leeds_Aus, I had use for your late post. Thanks :-) I do wonder how the proper maintenance of older kernels are, to prevent myself to get into a full boot-partion in the future.

---

### Post by rajhanschinmay on 2010-01-19
> **sdennie said:**
> What is the output of:

```

df

```



I have the same problem.
df command returns this:

Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda8             14421344   9438344   4250440  69% /
udev                   1786880       268   1786612   1% /dev
none                   1786880      1232   1785648   1% /dev/shm
none                   1786880       324   1786556   1% /var/run
none                   1786880         0   1786880   0% /var/lock
none                   1786880         0   1786880   0% /lib/init/rw
none                  14421344   9438344   4250440  69% /var/lib/ureadahead/debugfs
/dev/sda7                93307     89061         0 100% /boot
/dev/sda10            55431484  21572244  31043452  41% /home


so please let me know what to do.

is there any way of removing multiple versions.

I earlier had old version of Ubuntu.
Recently upgraded to 9.10. so if it is possible to remove any folders from /boot/ folder, please let me know.

---

### Post by some_girl on 2010-02-14
> **Jamo_Leeds_Aus said:**
> I have the same small boot partition for a raid set and had the same issue. Instead of RePartitioning everything , I went and deleted duplicates from my boot folder. IE latest versions were 2.6.28-14 so i deleted all 2.6.28-11. This allowed me to run the dpkg --configure -a without error and then use apt-get without issue. I know this is a late post but hopefully it may help someone.

Thanks from me too, that was much easier than changing partition sizes!

---

### Post by u-slayer on 2010-06-14
I'm getting these errors and I have 200MB for /boot! I thought that would be enough since I only have 22MB in use right now. This is kind of ridiculous.

How big should I make my /boot? 512MB... a gig???

---

### Post by u-slayer on 2010-06-14
bump

---

### Post by u-slayer on 2010-06-14
):p

---

### Post by ashrocks on 2010-11-15
I have a same problem like posted on the forum thread.
What iam doing exactly is:
My Debain OS crashed. I am taking backup in rescue mode, using debian installation disk.
Till now i was successfully able to mount the external hard drive to copy all the files on the root folder so that i can take backups.

I have mounted the external hard drive on /mnt/sda2
I need to copy all the files and directories into this folder (sda2).
But i cannot do anything other than "cp" or "cpio" command because it is in resuce mode, and i don't have any packages installed neither am i able to download any from "apt-get"
SO i guess i have to survive with "cp" command.

Everything worked fine, i was able to copy all the folders except "/opt" and "/proc"

My server is a SCSI RAID Hard drive with three partitions each mounted on 
/dev/cciss/c0d0p1      Mounted on : /
/dev/cciss/c0d0p3      Mounted on: /opt
/proc                        Mounted on: /proc

I want to copy all these files but unable to do so because it does not copy due to space requirements.
The total disk capacity of the files and directories on the root folder and other partition is about 60GB.

My hard disk capacity which i mounted has disk capcity of 250GB.
Why is it not allowing me to copy those folders. What is stopping it.
I have no idea. Any help leading to solve this issue will be highly appreciated.

I checked the disk space of external hard drive, it is hardly 600 MB and i have still 221Gb left in the dsik.

The error says:
gzip : stdout: No space left in the device

One quick doubt: Does it has to do anything with the directory i'm copying.
Coz root "/" is above the "/mnt/sda2" where i mounted my hard drive,

Thanks for reading :)

Ash

---

### Post by rieka2 on 2012-08-29
The /boot size on my system is 256meg and was set by autoconfig when the OS was installed. This seems to be a common problem when one applies every incremental patch and perhaps needs to be addressed by the developers who determine the minimum size of /boot when formatting the hard drive.  Another possible option might be to make /boot read only?

---

### Post by rickm1945 on 2012-08-29
I used the following: /  /Boot /Home /Swap. I always give 1024mbs to the /Boot Partition.
I know that's probably too much but I don't have any problems either. I have reinstalled Ubuntu 12.04 5 times now due to a variety of things I have tried to modify. So far I'm not messing things up so it  is running very good now. I have noticed though that even though I do clean installs of Ubuntu 12.04 each time I have installed it that their are previous files that appear without my having to install them again. Even after I delete the partitions and format them things show up again. I have no idea why.

---

