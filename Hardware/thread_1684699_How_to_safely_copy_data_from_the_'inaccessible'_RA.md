---
title: "How to safely copy data from the 'inaccessible' RAID hard disk?"
date: 2011-02-09
forum: Hardware
---

### Post by Iggy_White on 2011-02-09
Hello from a Linux newbie.

I need some clarifications about (not) destroying data on my hard disk. Any info is appreciated.

What's my problem: I have a disk that I cannot read anymore. It's removed from my WD MyBookWorld (blue rings). It's a single HDD raid array, it seems (that's what's its icon says in Nautilus). I was having 'access denied' messages from MBW, so I finally decided to remove it, copy the data to another disk and reformat the disk to normal filesystem. I don't think that disk has any physical damage.

I've read many, many posts on mybookworld.wikidot.com, but I'm still at loss as how to continue _safely_.

So what I need to know is:

if I use

# mknod /dev/md4 b 9 4
# mdadm—assemble /dev/md4 /dev/sdb4
# mkdir /media/xyz
# mount /dev/md4 /media/xyz
# chmod -R 777 /media/xyz

1) will my data be safe from damage if I'm not able to successfully copy the data, i.e. will I ba able to safely try it again using some different method?

2) can I use this method on an external disk attached via USB (so I don't have to open my machine to insert the disk)?

3) can I use 'mount -r ...' and still be able to use 'chmod ...' after that?

4) is there anything else I can try?

Bear in mind that I'm not a Linux guru (and I'm rather old :) ) so try to use simple words when explaining, please. :biggrin:

Thank you in advance for any help.

---

### Post by fjgaude on 2011-02-09
I'm not sure I can help but here goes: what makes you think this is a software raid disk? Only one disk in a raid array? Makes little sense.

Okay, you have taken the drive out of some external enclosure? And now can see the device as md4 in nautilus?

I have used mdadm for many years but never with only one partion, one drive.

Give us more info and maybe we can answer your concerns.

---

### Post by Iggy_White on 2011-02-09
From Wikipedia (original page [here]("http://en.wikipedia.org/wiki/Western_Digital_My_Book#World_Edition")):

"The disk filesystems are also known to exist in a format created by linux multiple devices driver ([Mdadm]("http://en.wikipedia.org/wiki/Mdadm"))  which ultimately wraps an ext3 partition with some metadata that allows  the inquiry of the position of the drive in a RAID set. Unfortunately,  this makes mounting the drives outside of the enclosure a bit more  complicated, it also requires a machine with a Linux (or possibly some  other Unix) based operating system."

So yes, it is a single-disk RAID in my case (I have MBW with single 1TB disk inside). And it's displayed as such in Nautilus, but initially it's of unknown type.

What more info might be useful? Can you please point me into what I might use to extract said info?

Thanks for helping.

---

### Post by fjgaude on 2011-02-09
Okay, but what makes you think this one terabyte (TB) you have is only one drive?

Please tell me what edition do you have?

I'm reading the wiki page at what this drive is all about! Wow!

I'm sure if you install gparted you will see just what is inside the drive, which likely will turn out to be at least two drives.

I have the knowledge to guide you through this without fear of loss of data but I have to fully understand first what we are working with.

---

### Post by Iggy_White on 2011-02-09
I know for a fact that I have just one drive because I disassembled the MBW and took the drive out. It's a WD Green Power 1TB SATA drive. I then put it into external USB HDD case (I can also use it as a standard internal drive, but I would like to avoid opening my machine if possible).

NAS I took the drive out is (or was) WD MyBookWorld edition (original, with concentric blue rings).

---

### Post by fjgaude on 2011-02-09
I think I'm getting it.

You have the single drive in a USB external case now. You are running a Ubuntu computer and when you see the drive in file manager it shows as "unkown type".

What shows when you run this from a terminal:

```
sudo fdisk -l
```

after you enter your password?

Do you have **mdadm** and/or **gparted** installed?

---

### Post by Iggy_White on 2011-02-10
Sorry for the delay, it's the timezone. :roll:

I forgot to mention that I use Ubuntu Live 10.10, as well as few other live Linux distros (Fedora 14, openSuSe 11.3, Debian 6.0).

Gparted is installed in Ubuntu, but not mdadm. Fedora has mdadm installed, but not gparted (only parted, command line).

Seems my MBW drive is listed as sdd. Here's what fdisk -l says about it (I can provide full listing if needed):

```

...
Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007a00

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1           48195     5927984     2939895   fd  Linux raid autodetect
/dev/sdd2         5927985     6136829      104422+  fd  Linux raid autodetect
/dev/sdd3         6136830     8112824      987997+  fd  Linux raid autodetect
/dev/sdd4         8112825  1953520064   972703620   fd  Linux raid autodetect

Disk /dev/md127: 1011 MB, 1011613696 bytes
2 heads, 4 sectors/track, 246976 cylinders, total 1975808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md127 doesn't contain a valid partition table

Disk /dev/md126: 996.0 GB, 996048437248 bytes
2 heads, 4 sectors/track, 243175888 cylinders, total 1945407104 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md126 doesn't contain a valid partition table

Disk /dev/md125: 106 MB, 106823680 bytes
2 heads, 4 sectors/track, 26080 cylinders, total 208640 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md125 doesn't contain a valid partition table
...
```From reading information on mybookworld.wikidot.com and martin.hinner.info/mybook/internals.php, I guessed that those three small partitions are MBW's system partitions (root, swap, data). Last, big /dev/sdd4 927GB partition corresponds to the PUBLIC share which was available to use for storing user data. I can confirm that this is indeed my data (cca 120GB free and cca 800GB in use). I need to copy data only from this last partition.

These are the screenshots from gparted (Ubuntu) and Disk Utility (Fedora):

[[IMG]http://i.imgur.com/85HoU.png[/IMG]]("http://imgur.com/85HoU")

[[IMG]http://i.imgur.com/sozAG.png[/IMG]]("http://imgur.com/sozAG")

Thank you for helping.

---

### Post by fjgaude on 2011-02-10
Okay, you have all the important infomation showing.

Seems the drive is more complex using **mdadm** then I've ever seen. It is a RAID-1 Mirror. That would suggest two drives but no, only one. Perhaps it's a 2TB drive partitioned into two TB ones. Strange! But no mind.

In Ubuntu install mdadm at a terminal command line:

```
sudo apt-get install mdadm
```

Then run this command and see what happens:

```
sudo mdadm --assemble --scan
```

That should get the array working as it did when you bought it. In nautilus ckick on the array as a normal drive, but likely with four partitions. Your data area will show and then you can copy the data to another drive if you wish. The USB connection will make things somewhat slow but you will have your data.

There's a change you will need to create a **/etc/mdadm/mdadm.conf** file manually, but let's wait and see if it is not auto-created.

You may wish to create a mount point but it's not necessary. Nautilus will show the array in the **/home/media** area with a large code number. You can leave it that way or create in **media** a directory name. We'll get to that later after the array is working correctly.

Let us know what happens.

---

### Post by Iggy_White on 2011-02-10
Thanks a lot, fjgaude!

Now, just to make sure - **mdadm --assemble --scan** - won't do anything funny to the drive/partition, right? Nothing will get overwritten or damaged? 

I know I sound paranoid, but I really don't want to lose data on this drive. :)

---

### Post by YesWeCan on 2011-02-10
[QUOTE=fjgaude]Seems the drive is more complex using **mdadm** then I've ever seen. It is a RAID-1 Mirror. That would suggest two drives but no, only one. Perhaps it's a 2TB drive partitioned into two TB ones. Strange! But no mind.[/QUOTE]

From: [http://wdc.custhelp.com/app/answers/detail/a_id/1522/related/1/session/L2F2LzEvdGltZS8xMjk3MzYwMTg0L3NpZC96YTdmQ2htaw%3D%3D](http://wdc.custhelp.com/app/answers/detail/a_id/1522/related/1/session/L2F2LzEvdGltZS8xMjk3MzYwMTg0L3NpZC96YTdmQ2htaw%3D%3D)
> If a single hard drive in the Dual-drive WD My Book World (Blue Rings) fails, you will not be able to upgrade the firmware of the device. The failed hard drive must be replaced before you can upgrade the firmware.

Could it be the case that this drive was originally one of a pair that had been configured for RAID1?

---

### Post by fjgaude on 2011-02-10
Right, no change in anything...  no possible damage or data loss.

The reason we are suggesting a "scan" instead of specifying the /dev/md126 array is the uncertainly of how all these partitions, arrays (three of them) were assembled originally. Let **mdadm** figure it out from the superblocks of each partition, array. Should be interesting.

If this doesn't work we can try the same --assemble command but add the -f to it, a force. Even that will not do anything to harm data on one of the arrays.

---

### Post by fjgaude on 2011-02-10
> **YesWeCan said:**
> From: [http://wdc.custhelp.com/app/answers/detail/a_id/1522/related/1/session/L2F2LzEvdGltZS8xMjk3MzYwMTg0L3NpZC96YTdmQ2htaw%3D%3D](http://wdc.custhelp.com/app/answers/detail/a_id/1522/related/1/session/L2F2LzEvdGltZS8xMjk3MzYwMTg0L3NpZC96YTdmQ2htaw%3D%3D)


Could it be the case that this drive was originally one of a pair that had been configured for RAID1?

I'll have to let Iggy_White answer if there were two drives or not.

---

### Post by Iggy_White on 2011-02-10
> **YesWeCan said:**
> Could it be the case that this drive was originally one of a pair that had been configured for RAID1?

No. But IIRC, there were two MBW editions: single-drive and dual-drive. I guess WD went the easy way and configured the system to be the same for both editions. That's why it looks strange for single-drive edition.

---

### Post by fjgaude on 2011-02-10
> **Iggy_White said:**
> No. But IIRC, there were two MBW editions: single-drive and dual-drive. I guess WD went the easy way and configured the system to be the same for both editions. That's why it looks strange for single-drive edition.

I wonder why Disk Utility shows the array as "degraded". Even if it is the command --scan will allow the array to come up and you should be able to get the data you want from it.

Time to do it! <smile>

---

### Post by Iggy_White on 2011-02-10
> **fjgaude said:**
> Right, no change in anything...  no possible damage or data loss.

The reason we are suggesting a "scan" instead of specifying the /dev/md126 array is the uncertainly of how all these partitions, arrays (three of them) were assembled originally. Let **mdadm** figure it out from the superblocks of each partition, array. Should be interesting.

If this doesn't work we can try the same --assemble command but add the -f to it, a force. Even that will not do anything to harm data on one of the arrays.

Thanks a lot again.

Just one additional question before I start: I'm downloading the latest (from today) natty-alternate-i386.iso. It has both mdadm and gparted, so if it's a live CD, I can use it instead of the default image (ubuntu-10.10-desktop-i386.iso) to boot Ubuntu. Is it a live CD?

---

### Post by YesWeCan on 2011-02-10
> **Iggy_White said:**
> No. But IIRC, there were two MBW editions: single-drive and dual-drive. I guess WD went the easy way and configured the system to be the same for both editions. That's why it looks strange for single-drive edition.
That is an interesting possibility. You mean their single disk units might be shipped as degraded RAID 1 disks? 
I'm not so sure because this would lead to the sort of problems you have encountered and I would have expected WD to preformat in Windows NTFS rather than linux format. Curious.

---

### Post by YesWeCan on 2011-02-10
> **fjgaude said:**
> I wonder why Disk Utility shows the array as "degraded". Even if it is the command --scan will allow the array to come up and you should be able to get the data you want from it.
Oh, because when disk utility detects a RAID1 disk and cannot find its mate it will called this a degraded RAID. As you say, mdadm should be able to assemble it and then Iggy can mount the degraded array and read the data. Fingers crossed.

---

### Post by Iggy_White on 2011-02-10
> **YesWeCan said:**
> That is an interesting possibility. You mean their single disk units might be shipped as degraded RAID 1 disks? 
I'm not so sure because this would lead to the sort of problems you have encountered and I would have expected WD to preformat in Windows NTFS rather than linux format. Curious.

There are many different performance problems with MBW devices. For example, they have gigabit ethernet chip installed, but for some reason (maybe the one you just mentioned?), read/write ratios are AWFUL, more like 100 mbit or even less.

As for why it's not ntfs - I guess embedded windows systems are not as good as Linux, are they? ;)

---

### Post by fjgaude on 2011-02-10
> **Iggy_White said:**
> Thanks a lot again.

Just one additional question before I start: I'm downloading the latest (from today) natty-alternate-i386.iso. It has both mdadm and gparted, so if it's a live CD, I can use it instead of the default image (ubuntu-10.10-desktop-i386.iso) to boot Ubuntu. Is it a live CD?

It is more complex using the LiveCD and I tell you I have natty alpha-2 on my system and it is very, very unstable.

All you need on your normal system is to install **mdadm** and do the --scan command.

Pray tell, why do you wish to use a LiveCD? Not because of having to install mdadm on your normal hard drive?

---

### Post by fjgaude on 2011-02-10
> **Iggy_White said:**
> There are many different performance problems with MBW devices. For example, they have gigabit ethernet chip installed, but for some reason (maybe the one you just mentioned?), read/write ratios are AWFUL, more like 100 mbit or even less.

As for why it's not ntfs - I guess embedded windows systems are not as good as Linux, are they? ;)

For a NAS you have to have a full-blown OS installed and Windows is not free, Linux is.

What main computer are you using, Iggy?

---

### Post by Iggy_White on 2011-02-10
> **fjgaude said:**
> It is more complex using the LiveCD and I tell you I have natty alpha-2 on my system and it is very, very unstable.

All you need on your normal system is to install **mdadm** and do the --scan command.

Pray tell, why do you wish to use a LiveCD? Not because of having to install mdadm on your normal hard drive?

No, nothing like that. I already have 2 windows installations on 2 different drives (XP and 7/64) and I don't want to additionally screw something up before I restore my data.

There is also nothing mysterious about the data - I'm a home audio recording enthusiast and all my works are stored on that drive (except for the song I currently work on). So you understand why I cannot lose it. :)

---

### Post by Iggy_White on 2011-02-10
> **fjgaude said:**
> For a NAS you have to have a full-blown OS installed and Windows is not free, Linux is.

What main computer are you using, Iggy?

Home made PC with 3 internal sata drives (barracudas), 2 dvds, Gigabyte GA-MA790X-DS4 MOBO, Phenom X4 9600 quad-core CPU, 8 GB PC-6400 DDR2 RAM, GeForce GTS250, 600W PSU with 4 additional low-noise fans. And few external USB drives for lugging stuff around. Nothing fancy. Rather old, to be honest.

---

### Post by Iggy_White on 2011-02-10
Okay, mdadm installed.

So, I don't need to specify any device for mdadm? 

**sudo mdadm --assemble --scan** will suffice?

---

### Post by fjgaude on 2011-02-10
Well, no. But you may wish to re-boot after installing it before running the command.

Your main computer is a laptop running Windows?

---

### Post by Iggy_White on 2011-02-10
> **fjgaude said:**
> Well, no. But you may wish to re-boot after installing it before running the command.

Your main computer is a laptop running Windows?

No, as I said above, home made desktop PC.

But won't I lose everything installed after rebooting? I run Live CD.

---

### Post by YesWeCan on 2011-02-10
As a precursor to assembling the array (of one disk) you can try

'sudo mdadm --examine --scan'

and post the output here.

This will show you what software RAID devices can be detected and details about them. This will not change anything on your disks.

---

### Post by fjgaude on 2011-02-10
> **Iggy_White said:**
> No, as I said above, home made desktop PC.

But won't I lose everything installed after rebooting? I run Live CD.

Gosh, sorry didn't see your earlier post. No, gigabit LAN, eh?

Okay, LiveCD... if you reboot you'll have to re-install **mdadm**. Gosh, all along I thought you had both Ubuntu and Fedora installed on your main computer. Now what to do?

In the LiveCD can you see the raid arrays? Yes, if the earlier **sudo fdisk -l** was from a command line terminal in the LiveCD.

---

### Post by Iggy_White on 2011-02-10
> **YesWeCan said:**
> As a precursor to assembling the array (of one disk) you can try

'sudo mdadm --examine --scan'

and post the output here.

This will show you what software RAID devices can be detected and details about them. This will not change anything on your disks.

Thanks, will try that.

---

### Post by Iggy_White on 2011-02-10
> **fjgaude said:**
> Gosh, sorry didn't see your earlier post. No, gigabit LAN, eh?

Okay, LiveCD... if you reboot you'll have to re-install **mdadm**. Gosh, all along I thought you had both Ubuntu and Fedora installed on your main computer. Now what to do?

In the LiveCD can you see the raid arrays? Yes, if the earlier **sudo fdisk -l** was from a command line terminal in the LiveCD.

Actually, I have 2 gigabit adapters in my PC. :D

Good point, though. I should definitely install Ubuntu on my spare partition one of these days. I still own prehistoric Slackware CDs with v0.94 kernel somewhere, as I was playing with Linux many, many years ago. But I somehow went away and never properly came back <blush>. Time to come back, it seems. :D

Yes, I can see raid arrays from my Live CD. I write this from Ubuntu. This is what I can see now (there's a USB stick attached now, that's why MBW drive is now sde):

...
Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00007a00

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               4         369     2939895   fd  Linux raid autodetect
/dev/sde2             370         382      104422+  fd  Linux raid autodetect
/dev/sde3             383         505      987997+  fd  Linux raid autodetect
/dev/sde4             506      121601   972703620   fd  Linux raid autodetect
...

---

### Post by Iggy_White on 2011-02-10
I'm not afraid to install Linux, it's just that stupid Windows 7 didn't ask where to install its boot data, so it chose the drive on which it is NOT installed... :-/

I will choose dual-boot on my WinXP partition, I guess.

---

### Post by Iggy_White on 2011-02-10
This is what I've got:

ubuntu@ubuntu:~$ sudo mdadm --examine --scan
ARRAY /dev/md126 level=raid1 num-devices=2 UUID=8062d58c:3cdcc748:699e24a7:bfd206c6
ARRAY /dev/md125 level=raid1 num-devices=2 UUID=81bc1109:ac11419c:374bd410:70d8c529
ARRAY /dev/md127 level=raid1 num-devices=2 UUID=80103611:399c4dc6:562340fb:cefe1b04
ARRAY /dev/md126 level=raid1 num-devices=2 UUID=37302007:e39bf9b5:01e225f3:e8c7642a
ubuntu@ubuntu:~$

---

### Post by fjgaude on 2011-02-10
Okay, from the LiveCD assemble or examine the array(s), and show us the results.

What I'm thinking about now is how to mount them so you can copy the data to your main computer. <smile>

---

### Post by Iggy_White on 2011-02-10
> **fjgaude said:**
> Okay, from the LiveCD assemble or examine the array(s), and show us the results.

What I'm thinking about now is how to mount them so you can copy the data to your main computer. <smile>

Damn... NTFS volumes are read-only?

---

### Post by Iggy_White on 2011-02-10
I have one spare external USB 320GB drive that I can format as FAT32. I could use that as a 'buffer'.

---

### Post by fjgaude on 2011-02-10
> **Iggy_White said:**
> I'm not afraid to install Linux, it's just that stupid Windows 7 didn't ask where to install its boot data, so it chose the drive on which it is NOT installed... :-/

I will choose dual-boot on my WinXP partition, I guess.

If you wish to install Ubuntu 10.10 the grub menu will pick Windows and you can multi-boot from its menu. Never try to install Windows on a system that already has Linux, that's when the boot partition is messed up.

There is another option: install 10.10 from the LiveCD onto a USB drive, 2 or more GB. Then boot from that drive which will have extra space to store everything on. If you have a 4GB one that would really do the trick. Only Ubuntu 10.10 lets you do such a thing. During the live install you can select the USB drive at the bottom of the main partition install menu, after selecting "manual" as the process.

The Alternate CD is not live if memory serves me. I haven't use Alternate for several years now so I'm not sure about 10.10 Alternate. Don't consider 11.04.

---

### Post by fjgaude on 2011-02-10
We are overlapping our posts... yes, the 32GB USB is nice. By installing Ubunut onto it you have a full running system with lots of data space. When you boot your computer you will have to tell it to boot from the USB drive and not the hard drive. Most BIOSs let you hit F12, that's Gigabyte's standard.

After booting all your drives will show, even the NTFS ones! Linux is smart, at least it has been for the last three or so years.

---

### Post by Iggy_White on 2011-02-10
> **fjgaude said:**
> We are overlapping our posts... yes, the 32GB USB is nice. By installing Ubunut onto it you have a full running system with lots of data space. When you boot your computer you will have to tell it to boot from the USB drive and not the hard drive. Most BIOSs let you hit F12, that's Gigabyte's standard.

After booting all your drives will show, even the NTFS ones! Linux is smart, at least it has been for the last three or so years.

Yes, I can see all my volumes even now. And yes, good idea - I can definitely install Ubuntu on this 320gig drive. Will do that right away! And yes, I use F12 to boot different OSes. :)

---

### Post by YesWeCan on 2011-02-10
> **Iggy_White said:**
> Damn... NTFS volumes are read-only?
They have probably been mounted as read only by the live CD in order to prevent people from accidentally overwriting something important on their Windows installations.
I think as root you can do whatever you want. I imaging you can do 'sudo cp -ar ...' to the NTFS partition of choice or perhaps remount it.

It would be prudent to format the external USB drive and use that. Format it as NTFS, though, not FAT32.

---

### Post by YesWeCan on 2011-02-10
Or install Ubuntu on it if you like!
But note that you will need you data on an NTFS partition eventually so Windows can read it.

---

### Post by Iggy_White on 2011-02-10
> **YesWeCan said:**
> Or install Ubuntu on it if you like!
But note that you will need you data on an NTFS partition eventually so Windows can read it.

Yeah, that's why I wanted to format it as FAT32, so both Linux and Windows can see and use it.

So, how much disk space is enough for ubuntu to happily install? I guess 10gigs should be enough. Plus how much for the swap? 512 megs or more? Do I need 3rd partition for /var, or should I stick with root + swap only?

---

### Post by YesWeCan on 2011-02-10
Ubuntu can read and write NTFS.

I am not sure I can advise you on partition sizes. It is so dependent on what you want to use it for. I'd go for 20GB minimum for everything. The basic install will consume about 3GB.

Ubuntu will run slowly off a USB disk because USB is quite slow. This may not be a good place for a permanent installation.

---

### Post by Iggy_White on 2011-02-10
> **YesWeCan said:**
> Ubuntu can read and write NTFS.

I am not sure I can advise you on partition sizes. It is so dependent on what you want to use it for. I'd go for 20GB minimum for everything. The basic install will consume about 3GB.

Ubuntu will run slowly off a USB disk because USB is quite slow. This may not be a good place for a permanent installation.

This will just be a temporary installation so I can safely move data, but still have the option of installing something and not bothering with a CD. I will later install it on an internal hdd.

And good thing about NTFS r/w :) One thing less to worry about :D

---

### Post by Iggy_White on 2011-02-10
Btw, did you see the output in Post [#31]("http://ubuntuforums.org/showpost.php?p=10446654&postcount=31")? Is that how it should be?

---

### Post by fjgaude on 2011-02-10
> **Iggy_White said:**
> Yeah, that's why I wanted to format it as FAT32, so both Linux and Windows can see and use it.

So, how much disk space is enough for ubuntu to happily install? I guess 10gigs should be enough. Plus how much for the swap? 512 megs or more? Do I need 3rd partition for /var, or should I stick with root + swap only?

I believe it would be better to install as ext4 and let Linux handle the NFTS file system.

Install as boot / and use the whole USB drive. After you boot from it you can use gparted to create other partitions, re-sizing the OS to about 4GB. The swap will automatically be handled. Under Ubuntu you will be able to write and read from your NTFS drives.

Gosh, this has been a long thread just because the hardware supporting mdadm raid failed.

---

### Post by Iggy_White on 2011-02-10
> **fjgaude said:**
> I believe it would be better to install as ext4 and let Linux handle the NFTS file system.

Install as boot / and use the whole USB drive. After you boot from it you can use gparted to create other partitions, re-sizing the OS to about 4GB. The swap will automatically be handled. Under Ubuntu you will be able to write and read from your NTFS drives.

Thanks, will do that.

> **fjgaude said:**
>  Gosh, this has been a long thread just because the hardware supporting mdadm raid failed.

I'm sorry for taking so much of your time. But I'm **really** grateful. Next time both of you come to Croatia you'll get beer and a kebab. And you'll be among first to listen to my music should I ever finish something and publish it online. :mrgreen:

---

### Post by fjgaude on 2011-02-10
> **Iggy_White said:**
> Btw, did you see the output in Post [#31]("http://ubuntuforums.org/showpost.php?p=10446654&postcount=31")? Is that how it should be?

After Iggy has a Linux system booting he will still have to run **mdadm** and assemble the array. Then copy that data to his NTFS file system. I believe all this can happen using Nautilus file manager in Ubuntu 10.10.

So much to learn to handle these kinds of things, eh?

---

### Post by fjgaude on 2011-02-10
> **Iggy_White said:**
> Thanks, will do that.

I'm sorry for taking so much of your time. But I'm **really** grateful. Next time both of you come to Croatia you'll get beer and a kebab. And you'll be among first to listen to my music should I ever finish something and publish it online. :mrgreen:

Okay, I'd like to hear such music.

---

### Post by Iggy_White on 2011-02-10
> **fjgaude said:**
> After Iggy has a Linux system booting he will still have to run **mdadm** and assemble the array. Then copy that data to his NTFS file system. I believe all this can happen using Nautilus file manager in Ubuntu 10.10.

So much to learn to handle these kinds of things, eh?

I'm constantly learning. My tombstone will be my diploma. :)

---

### Post by Iggy_White on 2011-02-10
> **fjgaude said:**
> Okay, I'd like to hear such music.

Well, if you're into progressive hard rock/metal, you might like it. If it's any good, that is. :mrgreen:

---

### Post by fjgaude on 2011-02-10
From the LiveCD can you see in the file manager, Nautilus, the NTFS drives, partitions?

---

### Post by Iggy_White on 2011-02-10
> **fjgaude said:**
> From the LiveCD can you see in the file manager, Nautilus, the NTFS drives, partitions?

Yes, all of them. And you are right, of course, they are read/writable.

Installing Ubuntu on my external USB drive at the moment.

---

### Post by YesWeCan on 2011-02-10
> **Iggy_White said:**
> This is what I've got:

ubuntu@ubuntu:~$ sudo mdadm --examine --scan
ARRAY /dev/md126 level=raid1 num-devices=2 UUID=8062d58c:3cdcc748:699e24a7:bfd206c6
ARRAY /dev/md125 level=raid1 num-devices=2 UUID=81bc1109:ac11419c:374bd410:70d8c529
ARRAY /dev/md127 level=raid1 num-devices=2 UUID=80103611:399c4dc6:562340fb:cefe1b04
ARRAY /dev/md126 level=raid1 num-devices=2 UUID=37302007:e39bf9b5:01e225f3:e8c7642a
ubuntu@ubuntu:~$

I am not an expert on these things but this list looks odd. There are two entries for /dev/md126 with different uuids. This seems to be telling mdadm to mount two different arrays to the same point.

Would you post the output of 'sudo blkid'?

---

### Post by Iggy_White on 2011-02-10
Funniest thing...

I successfully executed mdadm --assemble --scan. This was what I got:

[root@localhost liveuser]# mdadm --assemble --scan
mdadm: /dev/md/125_0 has been started with 1 drive (out of 2).

Then I successfully mounted the /dev/md126 volume. It was mounted as /media/63c1aa50-5108-4cda-adba-f012793129aa. So far so good. Never mind the strange name.

Now, from Nautilus I cannot access data. From Terminal, I can. Copied some data using cp, everything went fine.

At least I can now save the data (so far so good), though not in very elegant manner. But that's not important anyway.

Thank you both **very, very** much for all the help and for your time. 

Will inform you if everything went well.

---

### Post by Iggy_White on 2011-02-11
All data successfully saved!

Thanks once again for all your time and help, guys. Much appreciated.

---

### Post by YesWeCan on 2011-02-11
Glad to hear it.

---

### Post by fjgaude on 2011-02-11
You likely have a permissions issue with not being able to copy data using Nautilus.

Try the terminal command:

```
sudo chmod -R 777 /media/63c1aa50-5108-4cda-adba-f012793129aa
```

This will give you permission to do as you please with the entry.

I had a feeling that the --scan command would find all the arrays and you would know the one that has all the data.

Happy you have your music back, even if it is coming slowly.

These forums are to help folks that ask for it. <smile>

BTW, if you wish to use that drive for normal use you have to zero out the superblock before you can even format it.

```
sudo mdadm --zero-superblock /dev/md126
```

Let us know if you need anything else.

---

