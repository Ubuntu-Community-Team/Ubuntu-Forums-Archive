---
title: "install mistake"
date: 2009-09-14
forum: Installation &amp; Upgrades
---

### Post by stealthc on 2009-09-14
A user on my computer thought it would be handy to install ubuntu on a thumb drive.  Then when computer restart, it messed up my mbr and won't load.  Get grub error 21.

I would like to get vista back on my computer without nerfing it.  I have an asus g50v series laptop and lots of data on my drive, and asus is retarded their recovery disks will wipe all the data from my laptop; which is unacceptable.

Had asus gave me an emergency recovery disk like the one that comes with the retail version, I wouldn't have this problem because I could run bootrec.exe.  How do I undo the damage that this has done?

I'm currently in the middle of looking for a recovery disk, it would appear to be downloadable via bit torrent from this site:
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

So as I understand it, since this problem is new to me, I burn the iso and then I use bootrec.exe /fixmbr to solve this problem?

If so then I'll have this one licked in 15-20 minutes, but aside from that, does anybody have any thoughts as to how this can be accomplished from within linux if this idea fails?  Does ubuntu backup the mbr and if so can I restore this backup, and if not, why the heck doesn't ubuntu do that?

I am trying to do this without installing ubuntu... it won't let me eject the cdrom :(

---

### Post by cariboo on 2009-09-14
If you can boot from the Live Cd have a look at this [page]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/").

There are so many different ways to fix the mbr, it's hard to settle on just one. :)

---

### Post by 73ckn797 on 2009-09-14
Super Grub Boot disk is another solution.

Here: [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/) for the iso and then burn. Boot from that and you can restore from there.

---

### Post by stealthc on 2009-09-14
ugh.... I'm using a livecd, it won't let me eject the cdrom, I cannot burn a disk if I can't stick a blank in.

I tried downloading ms-sys, it wouldn't allow me because it wouldn't find it.  so I went looking for the download, found it, but it won't compile using the make command, also the instructions are wrong as they didn't note the directory is ms-sys-2.1.3

So any other ideas?

If I can just burn a disk I could try the windows vista x64 recovery iso that I downloaded.

---

### Post by stealthc on 2009-09-14
ok I've tried forcibly ejecting the cd-rom, won't work.

I've tried fdisk /dev/sdb
then installed using following options after deleting partitions
n,1,default,+750M,t,6
appears to have created fat 16 partition
n,2,default,default
appears to have created linux partition
w

writes, but then fails to mount and a window pops up indicating such.

Is there an easy way to make a linux os that will boot via thumbdrive, so that I may free up the cdrom and burn this iso file?

I've looked at toram option, but it seems awfully complicated.... that and they mention a .fs file which I cannot find so I pretty much get halted at step 1 of their crappy instructions.

:(

---

### Post by stealthc on 2009-09-14
ok I'll be more specific, does anybody know how I can get ms-sys working under the linux 9.04 livecd, since I cannot use sudo apt-get?  How can I compile it under that environment, the sourceforge page does not work one bit.

---

### Post by stealthc on 2009-09-14
I attempted to tweak the synaptics package manager, but to no avail, still cannot find ms-sys, obviously because it's down due to DMCA issues involving microsoft, downloaded the package found on the sourceforge page but it still won't compile, I have no clue what I have to do to get the make command to work for that after I've extracted it, entered ms-sys-2.1.3 folder and typed make.
always get an error message when I do that.

I'm going to try and install linux on a drive which has some extra space, hopefully this won't nerf anything further.... hoping this will fix this issue.

*Update, NOPE.  I'm not going to use the installers resize option for NTFS vista partition, I hear that may cause even more problems*

Does anyone here have any ideas?

---

### Post by stealthc on 2009-09-14
I've wiped a partition clean, boy it really sucks losing some of my data, but most of it was backed up a while ago, so hopefully that backup is still kicking around.

So here is the plan:
Try and solve the problem why my primary hard drive isn't being recognized, either through a bios option or my drive has slid out of the interface again :( so I will have to fix that.

Once this is fixed, I will proceed with an install of ubuntu 9.04 onto this freshly wiped partition, split the partition into three new ones.
One will be 10gb in size for the swap drive.
One will be 40gb in size for the ubuntu, and other files.
One will be 100gb as FAT 32 just in case NTFS in ubuntu poops out, this way there's an intermediary storage area that'll work just fine with the two operating systems.

After this is done I should be-able to burn the recovery disk, and then fix the mbr.

---

### Post by presence1960 on 2009-09-14
> **stealthc said:**
> I've wiped a partition clean, boy it really sucks losing some of my data, but most of it was backed up a while ago, so hopefully that backup is still kicking around.

That is unfortunate. All you need to do was download [this]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") Vista recovery console iso, burn it as an image to disk, boot the CD and then access Vista recovery console to restore your MBR.

Sorry I just clicked on your link, it is the same as I suggest.

---

