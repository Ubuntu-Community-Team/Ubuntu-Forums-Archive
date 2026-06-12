---
title: "Harddrive problems?"
date: 2015-09-04
forum: Hardware
---

### Post by leonard032 on 2015-09-04
So right now I'm dual booting lubuntu and Windows XP (for my games :D).

Just the other day I booted up the windows side and was met with an extremely slow desktop as well as a few weird errors. First that my avast! service wasn't started and second that my firewall was off. I figured I had managed to get a virus somewhere, but after a couple of scans, reinstalling avast and a couple *more* scans, and then installing Malwarebytes and another scan, it seemed the computer was clean.

So then tried to see if I could track down why the firewall wasn't starting. After lots of reading I narrowed it down to the Windows Network Connection Service, which wasn't running. I tried using the system file checker to replace any missing/broken system files, and manually starting the process, but I kept getting errors that the module was missing. Then I tried to replace the appropriate dll (netman.dll) with one from another computer. It wouldn't let me, I figured it was some automatic protection thing so I decided to do it from the lubuntu side. There I get another error, "Error opening file '/media/niall/4450E37150E3685E/WINDOWS/system32/netman.dll': Input/output error" So now I'm thinking it's a hardware problem, that the hard drive is starting to go.

Next I try booting up with a Parted Magic live CD and try to scan for hard drive errors that way. It says that the drive assessment is OK, but if I try to run a self-test, it fails. I then realized that lubuntu has it's own disk tools (duh, should have thought of the first...) so I boot up the lubuntu and mosey over to the disk's SMART Data page. The overall assessment is OK, with one bad sector, however when I start scrolling through the attributes I see some funny numbers. #187 Reported Uncorrectable Errors is 5057 sectors (increasing while I'm typing this), while #197 Current Pending Sector Count is 1, #198 Uncorrectable Sector Count is 1, but #5 Reallocated Sector Count is 0.

I'm getting the feeling that my hard drive is failing and I will be backing up all my important files, but I'm wondering if there is anything I can do.

---

### Post by TheFu on 2015-09-04
a) have good backups.
b) always scan windows from outside windows. That means booting off some other media to run the scans.

Linux has a tool called "bad blocks" which might be helpful. Definitely have good backups.

SMART is not very useful as a point-in-time.  Looking at the same data over months **is** useful.

---

### Post by weatherman2 on 2015-09-04
I agree that regular backups are essential, not just when you've noticed a hard drive problem.  By then it might be too late.

But I think S.M.A.R.T. is still very useful.  If you see one pending sector, that's a bad sign.  And if you can't run the short test, that's a really bad sign.  That's extremely helpful information from S.M.A.R.T. even now.

One pending sector means (at least) one sector has failed but cannot be read and replaced by the drive firmware.  It is "stuck."  If that sector is in some Windows system file, it may freeze when trying to boot or do anything.  One bad sector could indicate the drive is about to fail.  Sometimes if you zero out the whole drive you can clear these sectors and re-use the drive but not often.

I'd replace the hard drive ASAP myself, while you can still copy most of the data (try cloning the old drive to a new one, so you can just boot right off the new drive, both Windows and LInux.  Try Clonezilla).  Then once you've got all your data off the old drive for sure, try zeroing it out (write a zero to every sector with various tools or just use the Linux dd command to write /dev/zero to each sector).   Then check S.M.A.R.T. again.  If that pending sector hasn't cleared, recycle the drive.

---

### Post by leonard032 on 2015-09-04
> **TheFu said:**
> Linux has a tool called "bad blocks" which might be helpful. Definitely have good backups.

Thanks for your help. I ran bad blocks and it came up with four bad sectors, but I don't know what to do next. I did the command [here]("http://www.howtogeek.com/howto/37659/the-beginners-guide-to-linux-disk-utilities/")  to write the command to a flat file (whatever that is), but it just got hung up. I can't see what the ">" was supposed to be doing. Also he goes on to use fsck, which I believe is only for linux partitions.

> **weatherman2 said:**
> I agree that regular backups are essential, not just when you've noticed a hard drive problem.  By then it might be too late.

But I think S.M.A.R.T. is still very useful.  If you see one pending sector, that's a bad sign.  And if you can't run the short test, that's a really bad sign.  That's extremely helpful information from S.M.A.R.T. even now.

One pending sector means (at least) one sector has failed but cannot be read and replaced by the drive firmware.  It is "stuck."  If that sector is in some Windows system file, it may freeze when trying to boot or do anything.  One bad sector could indicate the drive is about to fail.  Sometimes if you zero out the whole drive you can clear these sectors and re-use the drive but not often.

I'd replace the hard drive ASAP myself, while you can still copy most of the data (try cloning the old drive to a new one, so you can just boot right off the new drive, both Windows and LInux.  Try Clonezilla).  Then once you've got all your data off the old drive for sure, try zeroing it out (write a zero to every sector with various tools or just use the Linux dd command to write /dev/zero to each sector).   Then check S.M.A.R.T. again.  If that pending sector hasn't cleared, recycle the drive.
Thanks for your help as well. That is pretty much what I plan on doing, if I can't get it to work any other way I'll use the zeroing method. I do think that the (a?) bad sector contained my network dll. When checking the properties on lubuntu the file show up as zero bytes and corrupted.

Also, I ran ntfsfix, but that didn't seem to do much, it only ran for about 2 seconds.

btw Reported Uncorrectable errors has made it to 5071 now.

---

### Post by weatherman2 on 2015-09-04
Why are you still using this drive?  Stop using it now - the longer you use it, the worse it could get, unless you have all important files already backed up and are willing to risk not being able to clone the operating systems...

---

### Post by TheFu on 2015-09-05
> **weatherman2 said:**
> Why are you still using this drive?  Stop using it now - the longer you use it, the worse it could get, unless you have all important files already backed up and are willing to risk not being able to clone the operating systems...

+100!!!!!!  You can attempt all the repairs you like - AFTER you get all the data is cloned somewhere else first. Do nothing else on that HDD except clone it to other storage.

---

### Post by leonard032 on 2015-09-05
Ok, well I'm going to be cloning the drive soon. Unfortunately I don't have any drives as big as the one I was using so I have to shrink the partitions. Hopefully things will still go OK. One thing I noticed is that the windows partition is the only one with errors, I would have thought everything on the drive was affected.

Ach. I can't resize the windows partition because of the errors. Looks like it will just need to be a full re-install.

---

### Post by TheFu on 2015-09-05
How were you doing daily backups without a drive large enough to hold all this stuff?

BTW, **fsarchiver** might be worth looking into. It will shrink backups and restore to smaller partitions - at least for Linux. I don't know what it can do for NTFS.

---

### Post by leonard032 on 2015-09-05
External (USB) hard drive, and I wasn't doing daily back ups...:?

Edit: I wasn't backing up everything either, just files like text documents, photos, etc, not programs or anything.

---

### Post by TheFu on 2015-09-05
Time and hassle vs storage space - that's the trade-off.  We all make it.

For Linux systems, I back up enough to restore the system in 30-45 min WITH all the data, settings, and programs like it was at 2am this morning. Do that daily and keep 60-120 days, depending on the risk factors for the system. Thanks to incremental backups, each system takes about 2-3 minutes daily.  Before I knew how easy it was, I didn't do it either.  I sleep much better now.  Have backups like that for about 20 systems here - they all fit into 500GB of storage.

For Windows, I do daily incremental backups of data and quarterly image-like backups - so I don't have to worry about the pain of reinstalling and reconfiguring all those programs again. The built-in backup tool from MSFT has screwed me over a few times, so don't trust it anymore.  Use partimage for about 5 yrs, but it is a real hassle. Requires booting a different OS just to make a backup. Yuck.  That's the problem with image-based backups.

Most of my systems run inside virtual machines, which is trivial 'image' backup/restore. Just copy the file(s) holding the VM when the VM is shutdown. I don't bother for Linux VMs, but for Windows, it makes life much easier - well - until MSFT screws us over, which has been happening more and more. For the Linux VMs, I treat them just like physical installs using the daily, incremental, dpkg --get-selections, /etc, /home, /var/.... method.  I've posted many examples in these forums - the backup scripts and the daily sizes of incremental backups.

Not all data is the same. Media (audio/video) isn't part of my daily backups and usually don't get any versioning. Podcasts or anything on a web streaming site don't need backups either - same for DVDs that I've moved online. The backup is the disc.  Things that are relatively small or change more than once a week/month ARE important and do get included in the daily backups.  Why daily?  Well, I used to do weekly backups and found the cost in storage between weekly and daily insignificant - why not?  Plus in my work life, I had 4 hr RTO and RPO design points, and learned that daily backups really aren't any more expensive to have - it is the less than 24 hr backups that get expensive.

---

### Post by weatherman2 on 2015-09-05
I don't value all of my data in the same way.  For "cannot replace" valuable data - pictures, tax info, etc. - I am religious about backups.  For other things that can be replaced - media, OS installs, etc. - I'm less careful.  Windows installs with activations and such can be very time consuming to re-install, so I do make image backups of them to save that hassle.

But hard drives are getting cheap enough that it's almost silly anymore not to have full backups of almost everything.

---

### Post by leonard032 on 2015-09-08
I ended up using ntfsresize with the --bad-sectors option to shrink the XP partition. Unfortunately I had more data than I thought so I had to delete some stuff. I follow [this]("http://ubuntuforums.org/showthread.php?t=1244058") to get the partition to match the filesystem. I'm not entirely sure if everything worked correctly though, as GParted didn't recognize the partition.
Anyway then I made a new partition on the new hard drive and started clonezilla. But now it seems stuck (see attached image). The remaining time is changing continuously, from 10 hours to 30 minutes.
I would expect that I could still clone the lubuntu partition, but I don't think there's any point as installing XP will remove it.

---

### Post by weatherman2 on 2015-09-08
If Clonezilla gets stuck, you can also revert to ddrescue, a tool requiring much more manual effort but can deal with bad sectors (skipping them or attempting to re-read them numerous times.

---

### Post by TheFu on 2015-09-08
partimage  - I never got clonezilla to work either.

---

### Post by weatherman2 on 2015-09-08
I've used Clonezilla numerous times to make images successfully from healthy disks (and then restored them and booted to test - even Windows 8 with secure boot worked fine.)  Clonezilla does have kind of a klunky user interface, but it works on a healthy disk.  I've never tried it on one with bad sectors.

---

### Post by leonard032 on 2015-09-08
Looks like ddrescue is working. Been at it for 11 inutes and it's found one error.
Now I'm wondering what exactly I'm going to have to do when this is done? I'd imagine I'll have to mess around the the grub and boot stuff. But I'm not sure what.

---

### Post by weatherman2 on 2015-09-08
I've never used ddrescue myself, but as I understand it, you would use it to save off an image of each partition, then try to use its logfiles to figure out which files would be corrupted.  Then you could restore each partition to a new drive.

Once you've copied over new partitions (and probably created a new swap for Linux), you'll need to do a few things on the Linux side:

1. Edit the /etc/fstab of the new / partition and update the UUIDs to match those from the new partitions you created.  Use the command "sudo blkid" to get the new UUID numbers (including swap.)

2. If you ever use hibernation, also update the file /etc/initramfs-tools/conf.d/resume to your new swap partition's UUID.

3. Run e2fsck on the restored Linux partition(s) .

4. Re-install / update Grub.  I like the "chroot" method - do a web search for "ubuntu grub chroot" and follow the recipe.

5. On the Windows side, run chkdsk to fix any file system problems there due to corrupt files.  It may not be able to fix the files but it should tell you which ones, if any, were corrupted.

---

### Post by leonard032 on 2015-09-10
Should I unplug the old HD, or does it not matter?

---

### Post by TheFu on 2015-09-10
> **leonard032 said:**
> Should I unplug the old HD, or does it not matter?

If the copy is done, yes. If not, no.
That disk might be fine - we just can't trust it anymore, at least not for anything important.

If the disk is near failure, leaving it spinning could be really bad.

---

### Post by leonard032 on 2015-09-10
> **TheFu said:**
> If the copy is done, yes. If not, no.
That disk might be fine - we just can't trust it anymore, at least not for anything important.

If the disk is near failure, leaving it spinning could be really bad.
Ok, I uplugged it. When all this is worked out I will probably try weatherman2's zero out method or something.

@weatherman2
I've done all the steps up to running chkdsk on windows. It doesn't seem to do anything, first of all it doesn't give me the option to select my which windows install to use (I remember it asking me which one before, even when there was only one option). Then, when running chkdsk it goes for a couple seconds and comes up with "there were some problems that couldn't be corrected" or something like that. (You would think I would learn to write notifications down by now, oh well)
It seems like it's not recognizing the windows partition is there. So I booted back into my lubuntu live CD and there is something weird going on with that partition.
I get this
```
lubuntu@lubuntu:~$ sudo fdisk -l

Disk /dev/loop0: 615.1 MiB, 644939776 bytes, 1259648 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sda: 111.8 GiB, 120060444672 bytes, 234493056 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa164c1df

Device     Boot     Start       End   Sectors  Size Id Type
/dev/sda1  *         2048 209717247 209715200  100G  7 HPFS/NTFS/exFAT
/dev/sda2       209717248 231346175  21628928 10.3G 83 Linux
/dev/sda3       231346176 234491903   3145728  1.5G 82 Linux swap / Solaris

Disk /dev/sdb: 14.9 GiB, 16025387008 bytes, 31299584 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000

Device     Boot Start      End  Sectors  Size Id Type
/dev/sdb1          32 31299583 31299552 14.9G  c W95 FAT32 (LBA)

Disk /dev/zram0: 1.2 GiB, 1300193280 bytes, 317430 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/zram1: 1.2 GiB, 1300193280 bytes, 317430 sectors
Units: sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes


```
which shows the NTFS partition.
But with parted
```
lubuntu@lubuntu:~$ sudo parted -l
Model: ATA SAMSUNG SP1213C (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size    Type     File system     Flags
 1      1049kB  107GB  107GB   primary                  boot
 2      107GB   118GB  11.1GB  primary  ext4
 3      118GB   120GB  1611MB  primary  linux-swap(v1)


Model: General USB Flash Disk (scsi)
Disk /dev/sdb: 16.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  16.0GB  16.0GB  primary  fat32        lba


Model: HL-DT-ST DVDRAM GSA-4167B (scsi)
Disk /dev/sr0: 724MB
Sector size (logical/physical): 2048B/2048B
Partition Table: mac
Disk Flags: 

Number  Start  End    Size    File system  Name   Flags
 1      2048B  6143B  4096B                Apple
 2      678MB  680MB  2327kB               EFI


Model: Unknown (unknown)
Disk /dev/zram0: 1300MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1300MB  1300MB  linux-swap(v1)


Model: Unknown (unknown)
Disk /dev/zram1: 1300MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End     Size    File system     Flags
 1      0.00B  1300MB  1300MB  linux-swap(v1)

```
it has the boot flag, which I added manually in GParted, but it doesn't recognize it as NTSF.
Any suggestions?

I'm off to work now.

---

### Post by weatherman2 on 2015-09-10
To be clear: you've copied the Windows partition to a new disk, and now you're trying to run chkdsk on it?  How?  Booting a Windows disc?  You do have to specify a drive letter in Windows (or maybe it defaults to C: - I don't remember).  If you boot a Windows disc, what was C: may be X: or something else while it is booted from the disc.

The boot flag is only required for booting Windows - no harm in adding it but isn't going to affect whether you can read the partition in Ubuntu or run chkdsk on it.

I would first make sure you can access your NTFS partition - let's say it's the main one that was C: - in Ubuntu.  Can you do that at all?  If not, you won't be able to run chkdsk in Windows, either.

I wouldn't bother running chkdsk on the old drive if that's what you are trying to do - only the new partition you have copied.

---

### Post by leonard032 on 2015-09-10
I was trying to run chkdsk from a cd on the new hard drive, after I copied the windows partition to it, ya. I can't access the NTFS partition from Ubuntu. At least not the way I did before, it used o show up as a large hard drive (much like my USB) that I could just click on in PcmanFm and it would load. It does not appear there anymore.

---

### Post by weatherman2 on 2015-09-10
As I don't know exactly what you did, what errors you got, etc, it's hard for me to know what to suggest.  Could be your NTFS partition had too many errors to be copied correctly.  If you used ddrescue to make a copy from one partition to the other, then you should be able to see it in Ubuntu.  chkdsk would only fix filesystem errors that were caused by bad sectors in files.

Assuming it's still on /dev/sda1 per your output, what happens if you type:

```

sudo mount /dev/sda1 /mnt ?

```

The fact that parted doesn't show it as an NTFS filesystem isn't good, though, I don't think (even though fdisk does).  I don't remember what controls that or how you might change it.

---

### Post by leonard032 on 2015-09-14
I get
```
lubuntu@lubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.


```
I can't boot the installed version of ubuntu either, grub won't appear. I've tried to fix/update grub two ways now [this]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") and [this]("http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/").
I'm wondering if the process I used and linked to in post #12 is the problem.

---

### Post by leonard032 on 2015-09-14
Also the boot-repair creates some boot logs. I just tried doing a purge of grub and reinstalling it as well as setting the boot flag to the Ubuntu (/sda2) (still wont boot to the os on the hard drive). It's log is paste.ubuntu.com/12413565
The older one was paste.ubuntu.com/12412268/
The other drive plugged in is just an external USB stick.

---

### Post by TheFu on 2015-09-14
> **leonard032 said:**
> I get
```
lubuntu@lubuntu:~$ sudo mount /dev/sda1 /mnt
mount: /dev/sda1 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error

       In some cases useful info is found in syslog - try
       dmesg | tail or so.


```
I can't boot the installed version of ubuntu either, grub won't appear. I've tried to fix/update grub two ways now [this]("http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd") and [this]("http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/").
I'm wondering if the process I used and linked to in post #12 is the problem.

Never use Linux file system tools to work on NTFS partitions. Didn't someone say that?  Always use the native OS for the file system and tools built for that OS to fix file system errors.

If your machine is UEFI, very few of the *google answers* will apply for how to fix boot issues. 
Sorry, I'm not any help.

---

### Post by leonard032 on 2015-09-14
I'm not using anything to try to fix file system errors, I'm just trying to get it to boot. When it finally does I'm planning to use windows tools to fix things.
Is my machine UEFI? I just looked that up and it seems to replace the BIOS, I have a BIOS.

---

### Post by leonard032 on 2015-09-18
I started a [new thread]("http://ubuntuforums.org/showthread.php?t=2295421") as this isn't really a hardware problem anymore.

---

