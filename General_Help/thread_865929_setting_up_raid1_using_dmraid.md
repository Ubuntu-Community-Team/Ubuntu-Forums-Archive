---
title: "setting up raid1 using dmraid"
date: 2008-07-21
forum: General Help
---

### Post by silentwol on 2008-07-21
Hi, this is my first post... I think this is the most appropriate forum, but please move it if it isn't :)

I'm try to set up two 250GB disks in a raid1 mirror. I want half the disk to be formated as NTFS and half ext3, so I can place important windows and linux files onto the mirror. No OS's will be installed on the disk, just data. Simple right?

I'm using my motherboard's (gigabyte 965p-ds3) fakeraid chip (jmicron), so I created an array in the bios, booted windows and everything was fine. I created a 150GB NTFS partition.

Next, I installed kubuntu on my other disk. Everything went fine. I following the fakeraid howto... Here's how I tried to set up the raid array on linux:
```

sudo dmraid -ay

fdisk
n (new partition)
p (primary partition)
2 (second partition)
[hit enter twice to fill up the rest of the disk]

sudo dmraid -r (reread partition table)
mkfs -t ext3 /dev/mapper/jmicron_GRAID2

added the following to fstab:
/dev/mapper/jmicron_GRAID2    /backup     ext3    defaults    0    2

sudo mkdir /backup

```

(above is typed up from memory, re-reading the guide.. I'm pretty sure this is exactly what I did)

Now, this all seemed to go OK, wihtout any errors.

However, on adding a file to /backup, it degrades the array. Not only that, but the bios reports that there are two raid arrays, with one disk in each them!

I tried rebuilding the array in the bios (deleting one array and then rebuilding the other). I rebooted into windows and everything seemed normal - I checked the disk manager and it reports one disk (the mirror) with an ntfs partition and an 'unkown' (ext3) partiton. So I then rebooted into linux and the test file was still there. So I touch'ed another file, rebooted and the array was degrated again (with the two mysterious arrays appearing in the bios again). I'm back in windows with the degraded array. The two raid disks are appearing in explorer as two seperate disks.

It seems linux isn't playing nicely :(

Any obvious faults?

Also, I'd ditch 'hardware' raid in a heartbeat if someone can point to software raid I can run in windows and linux at the same time (i.e. acheiving what I set out at the start of the post). Anyone know of a software solution?

Thanks,

Jack

---

### Post by silentwol on 2008-07-21
Any ideas?

---

### Post by Krupski on 2008-07-21
> **silentwol said:**
> I'm using my motherboard's (gigabyte 965p-ds3) fakeraid chip (jmicron), so I created an array in the bios, booted windows and everything was fine. I created a 150GB NTFS partition.

OK, I'm no Linux expert, but I have setup quite a few NAS (Network Attached Storage) boxes using Raid 1 so hopefully I can help you.

First of all, DO NOT use any "hardware" or motherboard RAID. Turn that off and setup your motherboard as normal IDE or AHCI drives (AHCI preferred if your mobo supports it).

Next, of course, the drives you are using for RAID need to be identical size.

Next, if you can afford to lose the data you already put on those drives, I would suggest these following steps (use sudo - or log in as root obviously):

(1) Unmount your RAID drive. Assuming your RAID device is called "/dev/md0" and assuming your mount point is "/home/shared", type the following command:

```

umount /home/shared

```

(2) Blank out the two hard drives in your RAID array. You don't need to erase them completely, just zero out the beginning. Assuming your two drives are called "/dev/sda" and "/dev/sdb", type the following command ([COLOR="Red"]**NOTE!!! This command will ERASE ALL DATA ON YOUR DRIVES!!! BE SURE YOU WANT TO ERASE THEM!!!**[/COLOR]). Also, be extra sure... double check that your device names are correct. They don't always come up the same with each boot... that's why UUID's are used instead of (unreliable) hard names.

```

[COLOR="Red"]**# WARNING! ERASES HARD DRIVES!!!**[/COLOR]
dd if=/dev/zero of=/dev/sda bs=1M count=1
dd if=/dev/zero of=/dev/sdb bs=1M count=1
[COLOR="Red"]**# WARNING! ERASES HARD DRIVES!!!**[/COLOR]

```

(3) Temporarily get rid of MDADM:

```

apt-get remove mdadm

```

(4) Get rid of MDADM's config file:

```

rm /etc/mdadm/mdadm.conf

```

(5) Temporarily comment out the reference to the RAID device in fstab:

```

nano /etc/fstab
(inside the editor, place a "#" in front of the "/dev/md0px" lines)
(press ctrl-o to save the file, ctrl-x to exit the editor)

```

(6) Reboot the computer:

```

reboot now

```

(7) Re-install MDADM:

```

apt-get install mdadm

```

...watch the progress and note that the install creates a NEW mdadm.conf file...

(8 ) Reboot again (sorry!)

```

reboot now

```

(9) Check that you now have a RAID device:

```

ls /dev/md0 <--should reply with: /dev/md0

```

...also make sure MDADM set it up as RAID-1...

```

cat /etc/mdadm/mdadm.conf

```

Look for something like THIS in the listing of "mdadm.conf":

```

# definitions of existing MD arrays
ARRAY /dev/md0 level=raid1 num-devices=2 UUID=8684a70e:b387a3aa:a4949914:14f104a3

```

Note your UUID will be different... you are looking for the "level-raid1" and "num-devices=2" part.


(10) Now run fdisk or cfdisk and create your partitions ON THE RAID DEVICE:

```

cfdisk /dev/md0

```

(11) Format your new partitions. Example: format your first partition as NTFS, the second one as EXT3:

```

mkfs.ntfs /dev/md0p1
mkfs.ext3 /dev/md0p2

```

If you get an error when trying to run "mkfs.ntfs", it's because it's not installed yet. To get it, install "ntfs programs":

```

# if necessary
apt-get install ntfsprogs

```

(12) Finally, add "/dev/md0p1" and "/dev/md0p2" to your fstab file... linking them to the directories you want them to be.

(13) Reboot. Linux should mount your new partitions and you're all set to use them.

If Linux needs to re-sync (re-build) the RAID array, you will know it because the hard drive light will be on. You can also check the status of a re-sync this way:

```

watch --i=1 /proc/mdstat

```

This will show a continuous update of what the raid driver is doing, updated at 1 second intervals. Use ctrl-c to exit the "watch" command.

Notice that you never had to use "mdadm -C ..." it got done automatically!

Good luck... I hope this helps you!

-- Roger

---

### Post by Krupski on 2008-07-21
> **silentwol said:**
> Also, I'd ditch 'hardware' raid in a heartbeat if someone can point to software raid I can run in windows and linux at the same time (i.e. acheiving what I set out at the start of the post). Anyone know of a software solution?


Check out this link: [http://www.vttoth.com/mirror.htm](http://www.vttoth.com/mirror.htm)

It shows you how to patch 3 files in Windows to enable software RAID... although accessing a Linux RAID array from Windows RAID probably won't be compatible...

---

### Post by silentwol on 2008-07-28
Krupski, thanks for your help :)

I put this little project to one side as I had other things to attend to...

Anyway, I've given up with dmraid, it was simply a nightmare! For anyone else whos trying, just give up, for the sake of your sanity. It seems pretty clear it's support for the jmicron chip is flakey at best, especially with raid1. Some people seem to have success with (pointless) raid0 though.

I've just set up software raid in linux and I'll just mount the windows partition and rsync any important files I want to backup :)

---

### Post by Mr. A on 2008-07-28
Krupski, regarding doing the software raid you suggested, instead of the FRAID he originally wanted to do I think.
Won't he have a booting problem with software raid if the main raid 1 mirrored drive fails?
From my tests on other OS like CentOS 5.2, and Fedora 9, the when a software raid (SRAID) is made use of, then your system will not boot if the first SATA drive fails.  Even if you have the /boot directory mirrored with RAID 1.
Please comment on making the system bootable regardless which drive fails if software raid is used to make raid 1 mirrors.  Or what should one do if the first drive fails?
My test show that the system boots fine when the second drive fails, and you can rebuild easy enough.  However, if the first drive is the failure, then it does not boot and sits there with only the word "GRUB" displayed.

---

### Post by Krupski on 2008-07-28
> **Mr. A said:**
> Krupski, regarding doing the software raid you suggested, instead of the FRAID he originally wanted to do I think.
Won't he have a booting problem with software raid if the main raid 1 mirrored drive fails?
From my tests on other OS like CentOS 5.2, and Fedora 9, the when a software raid (SRAID) is made use of, then your system will not boot if the first SATA drive fails.  Even if you have the /boot directory mirrored with RAID 1.
Please comment on making the system bootable regardless which drive fails if software raid is used to make raid 1 mirrors.  Or what should one do if the first drive fails?
My test show that the system boots fine when the second drive fails, and you can rebuild easy enough.  However, if the first drive is the failure, then it does not boot and sits there with only the word "GRUB" displayed.

Gosh... I honestly don't know.

I build NAS boxes and I put Ubuntu Linux 64 bit Server on 4 GB flash cards while the hard drives are configured as RAID devices.

The idea is that a hard drive may fail, but the solid state drive (the CF card) most likely will not fail and therefore I will always be able to boot.

I use MDADM raid to manage the hard drives - but there is no OS at all on the hard drives. They are all data. The OS resides on a Compact Flash card (installed in an Addonics CF to IDE adapter) [[COLOR="Red"]LINK[/COLOR]]("http://www.addonics.com/products/flash_memory_reader/adebidecf.asp")

I *assume* (and I can only assume since I've had no problems yet) that if a RAID drive fails, I'll get a warning emailed to me and I'll have a chance to replace the failed drive (which will then trigger a raid rebuild).

But, since the OS is on a different drive, a RAID failure shouldn't prevent me from booting.

Sadly, I don't know enough about Linux in general to offer any more help. I'm a newbie myself!  :)


-- Roger

---

