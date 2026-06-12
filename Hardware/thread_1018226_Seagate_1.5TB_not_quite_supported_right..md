---
title: "Seagate 1.5TB not quite supported right."
date: 2008-12-21
forum: Hardware
---

### Post by sigmason on 2008-12-21
I'm using 2 Seagate Barracuda 7200RPM SATA drives in a Dell PowerEdge SC440 on the onboard SATA ports (1 and 2 of 4) with a boot drive that is an Western Digital 80GB PATA drive on the 1st IDE channel as master.

The installation of Ubuntu 8.04LTS was fine.  We started having problems with the drives when we tried to partition them as 2 large EXT3 partitions (one per drive.)

Gparted was fine with partitioning the drives up to 1TB.  Regardless of setting the label to GPT or MS-DOS Gparted reported -1 sectors at even 1 sector beyond 1TB.

We tried manual partitioning with parted, fdisk, mkfs, mke2fs and so forth.  We could create and mount these partitions, even automount them in fstab, BUT unlike when gparted made a partition, the Computer File Browser in Gnome would show both the mounted partition and 1 "SCSI Drive" per drive for no apparent reason.  Again, if we make the partitions 1TB or smaller the "SCSI Drive" will disappear once the partitions mount.

I tried a ton of tricks.  I don't care that the drives are being labeled as SCSI as /dev/sdb and /dev/sdc, but I want the "SCSI Drive" icons that won't mount in File Browser to go away.  The only way to do that is apparently either split the drives into multiple partitions or not use the full capacity of the drives.  I tried this with the LiveCD for kicks as well.

What causes the Gnome File Browser to create the "SCSI Drive" icon when a drive is not formatted?  How do I get the one large partition because as I understand it GPT support is already compiled into the Ubuntu kernels?

Eventually I want to try to RAID these drives as a mirror with mdadm, but first I really want to be able to use them properly from inside Gnome without the additional icons to trip over.

By the way, gparted considers the greater then 1TB partitions corrupt, despite the fact that I can read and write to them no problem from the CLI.

I've also tried this with EXT2 and ReiserFS, same problem both times.

I thought it might just be Gnome, but in KDE the "SCSI Devices" don't appear, but then again, neither do the formatted partitions.

Any ideas?

Sigmason

---

### Post by IanW on 2008-12-22
You need to report this as a bug against GParted and possibly Nautilus.
It sounds like the developers have taken 1TB as the absolute max size a HDD can possibly be.
Obviously, this is no longer the case.

---

### Post by sigmason on 2008-12-22
First an addendum to my original post.

This issue is not related to the issue with the Seagate 1.5TB drives having bad performance and long delays on various distros of Linux, for which Seagate produced a firmware upgrade.

I tried upgrading the firmware of one of my SATA Seagate Barracudas from SD17 (what it came with) to SD1A which I got from the NewEgg site from which I bought both drives.

This firmware update had no effect on my original post.  Nor was I able to replicate this performance issue as it related to the drive's internal power conservation measures with either firmware.  Though my test data set was less then 20MB so that may account for this.

Sigmason

---

### Post by sigmason on 2008-12-22
Secondly, I agree with your analysis IanW, I was hoping that would not be the case and this wasn't a built-in issue.

It seems odd to me.  Hdparm didn't report anything that at first glance seemed too wildly out of whack.  Nor did any of the CLI programs refuse to complete.  I was not able to use parted to resize the partition made by gparted when it was 1TB.  I got told there was an incompatible feature, but to be honest that behavior I've seen before on drives much smaller so I can't attribute to that any major concern.

Fsck didn't report any major issues with the underlying file system either, even though gparted seemed to think the file system was hammered.  To add to this, gparted wasn't able to even fsck the partitions which is obviously just plain wrong.

Anyway, before I go off bug reporting...read my next post.

Sigmason

---

### Post by sigmason on 2008-12-22
So in eliminating my options, and after reading IanW's post I decided to try using Ubuntu 8.10 current instead of 8.04 LTS.

I've had problems before in which I've run into walls that magically go away with the more current build instead of the LTS builds and oddly enough this turned out to be another example.

The Ubuntu 8.10 build I downloaded and installed this morning changed everything.

When I run the 8.10 LiveCD I can see the primary drive as "79.5GB" and the 2 1.5TB drives as "1500GB" respectively.  I oddly see the boot "FileSystem" as well, but as a default that's probably in fstab and really how many boot drives am I going to replicate like that (maybe 1) so I can live with that.

When I double click on these icons it takes a second but they mount.  I did get told they weren't mounted once on each icon at first but that's probably my impatience in not waiting for the mounts to complete.

I could see the 1.5TB EXT3 partition on sdc and it was listed as labeled with GPT.  I could see the 1.5TB EXT3 partition on sdb and as I recall it was listed as labeled with MS-DOS (not sure about that, will update later).

Unfortunately, gparted still wouldn't make a partition over 1TB.  However, it didn't report the working partitions as bad as long as the drive label was GPT which I think makes sense (I'll update this later if I've got that wrong.)  However, this means that in 8.10 I CAN partition the drive labeled as GPT with a full 1.5TB EXT3 partition and it will read right in the "File Browser".  There were no "SCSI Drive" icons to be found.  The "74.5GB" boot drive did not appear in "File Browser" in 8.04 LTS.  I guess what ever they changed caused it to enumerate like this.

I will update this later, but for now, it would seem that if you have 1.5TB Seagate drives you should use 8.10 instead of 8.04 LTS and probably should call Seagate and update your drive firmware from SD17 to SD1A (you can check this with hdparm).  I would recommend calling Seagate only because there is more then one version of the update and the wrong version WILL brick your hard drive and probably void your warranty.

I'll do the actual install later and update this thread again.

Sigmason

---

### Post by sigmason on 2008-12-23
Okay an update.

I installed 8.10 to my primary 80GB PATA drive and discovered that the reason I was getting both the 74.5GB drive and the FileSystem icon in "Computer" when I booted from the LiveCD was because the LiveCD was the FileSystem and the 3 partitions on the 80GB drive were in fact not the boot FileSystem.  Silly, but when you stare at it long enough, it's an easy error to make.

It turned out that I did not need to label the drives as GPT in 8.10.  That in fact when I did label the drives as GPT was when they couldn't be partitioned or formatted in 8.10 over 1TB.  When the drives were labeled MSDOS they partitioned and formatted just fine even in gparted and from the CLI.  Keep in mind in 8.04LTS I couldn't create or format any partition...not EXT3, EXT2 or even ReiserFS as larger then 1TB regardless of the label being MSDOS or GPT.  At least in 8.10 the MSDOS labeled drives work over 1TB with EXT3.  Oddly in 8.10 with the label of GPT I could not make partitions over 1TB just like in 8.04LTS.

After I managed to get these 2 drives each with a single EXT3 partition and both with MSDOS labels.  I set them to automount in fstab using their UUIDs.  That all worked fine.  I could read and write and gparted had no problems in 8.10 like it did in 8.04LTS (it was reporting that the EXT3 partitions larger then 1TB were corrupt).

I then used used mdadm (why mdadm installs citadel with it seems very heavy handed to me so I removed citadel) to software mirror the 2 1.5TB drives together.  Currently one of the drives has firmware SD17 and the other SD1A.  I'm going to give it some 'burn in' and see if that causes any issues.

So I think I'm safe to say that if you plan on using these Seagate 1.5TB Barracudas in Ubuntu, use at least 8.10, label the drives with MSDOS (the default) type labels and everything else should be fine.

Sigmason

---

### Post by djbrettb on 2009-01-14
Could you maybe give a detailed description of how you got the drives to format successfully?  I'm running 8.10 server and I am running into the same problem you were.  Am I able to do what you did without the GUI, or do I need to be running the desktop version of Ubuntu?

---

### Post by sigmason on 2009-02-24
I just used gparted with the MSDOS label and formatted the volumes EXT3.  I am running software RAID, but prior to setting up mdadm I had both drives formatted standalone with no issues.

If you have the Seagate drives, please contact Seagate for the firmware update, if any.

Sigmason

I was able to do this from the command line with parted, fdisk, mkfs, mke2fs as well, so I don't think it matters if you use the Desktop or Server installation.

For kicks, you really don't need to reinstall the whole system to use the Desktop version, just use the LiveCD and I think you'll have gparted to work with.  This way you can use gparted, without reinstalling your server install.

---

### Post by pdub on 2009-03-01
I compiled and installed gparted 0.4.3 on Ubuntu 8.04 Hardy to resolve this issue.

[http://gparted.sourceforge.net](http://gparted.sourceforge.net)

---

