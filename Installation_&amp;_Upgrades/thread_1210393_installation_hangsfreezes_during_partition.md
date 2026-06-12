---
title: "installation hangs/freezes during partition"
date: 2009-07-11
forum: Installation &amp; Upgrades
---

### Post by ncumming on 2009-07-11
my system was running a little strange after upgrading from 8.10 to 9.04, so i decided to try a fresh install.  I dual boot xp and ubuntu, each on a separate internal SATA HDD.  when i get to the formatting step of the install (after i set up the partitions), the install hangs up while partitioning the portion of the drive i'm using for /home.  

I tried downloading another iso file and installing off a USB drive instead of CDROM and i get the same error.  any ideas as to what could be causing this?  

i'm running a dell 3 ghz p4 desktop with 4 GB of RAM.

After the system hangs up, depending on how long i let it sit, eventually i get an error that says something along the lines of "you were logged in for less than 10 seconds...your system may be corrupt"

---

### Post by merlinus on 2009-07-11
Try the text-based alternate install cd, which seemingly has less problems with sata hdds.

---

### Post by ncumming on 2009-07-11
ok i'll give that a shot next.  i've run hard drive diagnostics and didn't see any issues, and am running a memtest right now.

---

### Post by ncumming on 2009-07-12
just finished letting memtest run over night - 80,685,128 errors.  I'm guessing that isn't good.

---

### Post by ncumming on 2009-07-12
Turns out I had a bad memory module, which was probably what was causing the stability issues that prompted me to do a fresh install in the first place.  I removed the errant stick but i still have major issues.

I downloaded the alternate install cd but still get stuck during the partitioning/formatting step.  I get input/output errors that keep the partitioner from setting up partitions at all, or it runs for a while and says "error setting up partition on /dev/sdb" or "partition failed." 

Using a live CD, ubuntu can mount the NTFS partition of the SATA drive that i haven't been messing with.  But it can't mount the partition that i'm trying to install to.  I tried reformatting the partition, and didn't get any errors, but when i go back to the installer same result as before. 

I'm sure all of this is related to all of the installs i tried before i found i had bad memory.  Something strange happened to the disk that is keeping ubuntu from mounting it properly.  But i don't have a clue as to what to try next.

Any suggestions?

---

### Post by ncumming on 2009-07-13
Figured anyone who might know what's going on might ask this, so here's the output from fdisk-l:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19451   135757282+   f  W95 Ext'd (LBA)
/dev/sda5            2551       19323   134729091    7  HPFS/NTFS
/dev/sda6           19324       19451     1028128+   e  W95 FAT16 (LBA)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009965b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+   b  W95 FAT32
/dev/sdb2            1217       30401   234428512+   5  Extended
/dev/sdb5            5640       30401   198900733+   7  HPFS/NTFS
/dev/sdb6            1217        2432     9767457   83  Linux
/dev/sdb7            2433        2554      979933+  82  Linux swap / Solaris
/dev/sdb8            2555        5639    24780231   83  Linux

Partition table entries are not in disk order

```

any ideas?

---

### Post by merlinus on 2009-07-13
The problem may be, as fdisk says, that your partition table is not in order on sdb.

You might try this:

```
sudo fdisk /dev/sdb
m
x
f
w
```

---

### Post by ncumming on 2009-07-13
Thanks for the suggestion!

Since my last post, I restored the MBR so i could boot to XP, and attempted to reformat sdb from there.  There was a ~9GB partition at the beginning of the disk that gave me an error and crashed windows disk manager.  Only reason i mention that is the partitioning scheme on the disk is different now than i posted before.

So here's what i get when i tried those commands, followed by fdisk-l (I omitted the help listing for space):

```

Command (m for help): x

Expert command (m for help): f
Nothing to do. Ordering is correct already.


Expert command (m for help): w
The partition table has been altered!

Calling ioctl() to re-read partition table.
Syncing disks.
ubuntu@ubuntu:~$ sudo fdisk-l
sudo: fdisk-l: command not found
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   7  HPFS/NTFS
/dev/sda2            2551       19451   135757282+   f  W95 Ext'd (LBA)
/dev/sda5            2551       19323   134729091    7  HPFS/NTFS
/dev/sda6           19324       19451     1028128+   e  W95 FAT16 (LBA)

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0009965b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        1216     9767488+   6  FAT16
/dev/sdb2            1217       30401   234428512+   5  Extended
/dev/sdb5            5640       30401   198900733+   7  HPFS/NTFS


```

so you can see that when i ran the f command it said "nothing to do," but when i ran the "w" command it said changes have been made.  Not sure what happened, but the note about the partitions being out of order is gone.  I'm going to try to format the volumes again and see if it works before i try another install (crossing my fingers)...

---

### Post by ncumming on 2009-07-13
still think there is something weird going on.  when i run gparted, on sdb there is a section of unallocated space with an error message that gparted doesn't recognize the filesystem at the beginning of the disk - not part of the sdb "grouping."  I tried deleting the partition but that didn't really help anything.  Here's a screengrab from gparted:

---

### Post by merlinus on 2009-07-13
You might try moving sda5 to the beginning of the extended partition, so the ones you create will be in numerical order.  Otherwise, from what I see you will recreate the same situation.

Our last posts crossed, but gparted is echoing what I just said.

---

### Post by ncumming on 2009-07-13
No luck.  I used gparted to move sdb2 to encompass all of the unallocated space into one big "free space" block.  Then i tried to format that chunk to ext3, and got an error.  Now gparted doesn't see sdb at all any more, nor does fdisk.

---

### Post by merlinus on 2009-07-13
sdb2 already encompassed the unallocated space.  What I thought to do was have you move sdb5 to the front of sdb2, and then create partitions in the space at the end of sdb2.  Then they would have been numerically correct, beginning with sdb6.

At this point, if even the gparted live cd is not seeing sdb, it might be best to start over with a fresh install.

---

### Post by ncumming on 2009-07-14
> **merlinus said:**
> 
At this point, if even the gparted live cd is not seeing sdb, it might be best to start over with a fresh install.

I'll try another fresh install tonight, although I'm guessing the installer is going to get hung up again during the partitioning/formatting phase, which is what got me here in the first place.

Another idea - I've got all of the data on sdb5 (the xp/NTFS partition) backed up.  Could wiping the whole disk and formatting it all as one big partition be a quick way to get out of this mess?  Then when i run the installer, i'll delete the "big" partition and create new /,/home, swap, and NFTS partitions?


For what its worth, i ran a the disk utility on startup and the disk doesn't appear to have any "errors" on it.  So this seems like something i should be able to remedy one way or the other.

---

### Post by merlinus on 2009-07-14
Sounds like a good idea.  Format the partition as ntfs.  You will not haveto delete it, however -- at the parttioning screen you can set up your partitions using the entire disk.

Select manual, and specify the sizes for each.  / should be around 10G, 10G for /home, 1.5G for /swap, and the rest leave as ntfs so you can share data with windows.

Of course this depends upoin how much space you have...

---

### Post by merlinus on 2009-07-14
Forgot to mention to rightclick on each partition and/or select edit.  Choose use as ext3 (or ntfs for the shared partition), tick the format box, and choose mountpoint (/, /home, and perhaps /data for the shared one).

---

### Post by ncumming on 2009-07-14
Thanks. those are about the partition sizes i had guessed at using before, but its good to see confirmation.  Its a 250GB drive so there's plenty of space - i'll probably make /home a little bigger because i plan to do some video editing and i think i'll want to be working off an ext3 partition when i'm doing that, vs ntfs.

---

### Post by NinjaNumberNine on 2009-07-14
I had the same problem this week. I ended up installing ***[COLOR=Red][Mythbuntu]("http://www.mythbuntu.org/")[/COLOR]*** (I had done this in the past.) This is actually the easiest way, because ***[COLOR=Red][Mythbuntu]("http://www.mythbuntu.org/")[/COLOR]*** installs fast and once you are in the OS, you can go in Mythbuntu control center and because mythbuntu is relatively bare of features and has only XFCE as the display manager, there are three options to upgrade your system to:
#1 Xubuntu
#2 Kubuntu
#3 Ubuntu
This works great and within thirty minutes you will have whichever OS you want.


Lots of luck,

  NinjaNumberNine

P.S. The word Mythbuntu in the text is a hyperlink.

---

### Post by ncumming on 2009-07-14
another apparent dead end.  I got an error message from gparted when it was trying to delete the one of the partitions, but it continued to move on.  For about 5 hours its been stuck on the step "creating new ntfs file system."  I know it should take a while to format a 250GB drive but i wouldn't think that long.  I'm going to let it run over night but i think i'm back to the drawing board.  If by some chance it does complete the formatting step i'll try the OS install and post how it goes.

---

### Post by merlinus on 2009-07-14
Dead in the water.  It is much faster than that for basic formatting.  Are you using the gparted live cd, or the version on the ubuntu disk?

---

### Post by ncumming on 2009-07-15
I'm using the 9.04 live cd.  It never did finish formatting, so I finally closed it maually this morning.  After I stopped it, sdb stopped showing up altogether.  I'm sure if I tried a fresh install now I'd get an error/hang up during install.  So I'm totally out of ideas again.  Suggestions?

---

### Post by NinjaNumberNine on 2009-07-15
Were you trying  Mythbuntu?

---

### Post by NinjaNumberNine on 2009-07-15
Oh, and what kind of graphics card do you have? :-k

---

### Post by NinjaNumberNine on 2009-07-15
By the way, I hear you used 9.04. So far, based on my experience I find 8.10 to be far more stable for this reason:
When the designers engineered 9.04, they created a new proprietary driver in place of fglrx. See link below. 
  If you do have an AMD/ATI graphics card, click **[this link]("http://ubuntuforums.org/showthread.php?t=1213404&highlight=amd+radeon"). **

---

### Post by ncumming on 2009-07-15
I haven't got to the point of installing a new os yet because I figured it was pointless if the live cd couldn't mount/partition/format the drive.  I don't really see what the connection with the graphics card could be but I'm using an older 128mb card (its a dell dimension 8400 - ill have to dig a little to see exactly what card is in it.  If you think it might work I can press with a mythbuntu install - I'll try anything at this point.

---

### Post by NinjaNumberNine on 2009-07-15
I'm not a big fan of Mythbuntu as an OS, it is pretty ugly. But as for installing, it has never failed. You know how most distro's live cds have around six steps? I think that the reason Mythbuntu works is because it has 13 steps, and that confuses whatever keeps you from installing Ubuntu. Also, you can never tell that you even loaded mythbuntu once you upgrade it to Ubuntu in Mythbuntu Control Center.

---

### Post by NinjaNumberNine on 2009-07-15
Oh, and you can forget about the graphics card. If you don't know that you have an AMD, you probably don't. ;)

---

### Post by ncumming on 2009-07-15
Definately have an intel chip, I just couldn't remember who made the graphics card.  Ill give mythbuntu a shot and see what happens!

---

### Post by NinjaNumberNine on 2009-07-15
Have fun!

---

### Post by ncumming on 2009-07-15
No luck with mythubuntu - hangs up formatting the partition for /.

One development - after what I thought was a failed attempt to format the drive in gparted after a reboot (using live cd) I was able to mount and even write a file to the hard drive in question.  Not sure what that means other than there is something weird going on.

---

### Post by NinjaNumberNine on 2009-07-16
:confused:> No luck with mythubuntu - hangs up formatting the partition for /.:confused: :-k
Wow. If THAT didn't work, then you KNOW > there is something weird going on.     
I am temporarily out of suggestions, but I will be looking.

---

### Post by ncumming on 2009-07-16
I ran gparted again trying to format the drive.  This time i saved the details (duh) which i obviously should have done and posted here before.  Here are the results:
```
GParted 0.4.3

Libparted 1.8.8
Create Primary Partition #1 (ntfs, 218.44 GiB) on /dev/sdb  00:08:06    ( ERROR )
     	
create empty partition  00:00:10    ( SUCCESS )
     	
path: /dev/sdb1
start: 30282525
end: 488392064
size: 458109540 (218.44 GiB)
set partition type on /dev/sdb1  00:00:11    ( SUCCESS )
     	
new partition type: ntfs
create new ntfs file system  00:07:45    ( ERROR )
     	
mkntfs -Q -v -L "" /dev/sdb1
     	
Cluster size has been automatically set to 4096 bytes.
Creating NTFS volume structures.
Creating root directory (mft record 5)
Creating $MFT (mft record 0)
Creating $MFTMirr (mft record 1)
Creating $LogFile (mft record 2)
Creating $AttrDef (mft record 4)
Creating $Bitmap (mft record 6)
Creating $Boot (mft record 7)
Creating backup boot sector.
Creating $Volume (mft record 3)
Creating $BadClus (mft record 8)
Creating $Secure (mft record 9)
Creating $UpCase (mft record 0xa)
Creating $Extend (mft record 11)
Creating system file (mft record 0xc)
Creating system file (mft record 0xd)
Creating system file (mft record 0xe)
Creating system file (mft record 0xf)
Creating $Quota (mft record 24)
Creating $ObjId (mft record 25)
Creating $Reparse (mft record 26)
Syncing root directory index record.
Syncing $Bitmap.
Syncing $MFT.
Updating $MFTMirr.
Syncing device.
Syncing device. FAILED

========================================
```

So the error is occuring at "syncing device."  Not sure if that helps anyone or not.  :-k

---

### Post by NinjaNumberNine on 2009-07-16
You have more Beans than I do- lets wait for Merlinus. :lolflag:
Wish I could help... Say,  you did use Mythbuntu 8.10, right?

---

### Post by ncumming on 2009-07-17
well for anyone out there following this thread i am officially giving up.  just downloaded and ran killdisk at one more (in hindsight futile) effort to try to erase this disk and make it useable again, and even that hangs up.  So its off to the recycling bin for this drive.  Now it seems cheap to pay $80 for a new drive.  I'd pay twice that to get the last week of my life back...

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

---

### Post by ncumming on 2009-07-17
and look at that, i can't even insert an emoticon properly...
:confused:

---

### Post by merlinus on 2009-07-17
Sorry to hear that.  But on the somewhat brighter side, I imagine you learned a great deal in the process, which hopefully will serve you well in future.

FWIW, when I first started using ubuntu I had to reinstall four or five times because of all the learning situations I created!

Good luck!

---

### Post by ncumming on 2009-07-18
I certianly learned a thing or two.  Just frustrating to get to the end of something like this amd not be 100% sure whether it really is a hardware problem or if it was something that ultimately would have been fixable.  I hate surrenduring!   Thanks for all of your help, its a good feeling when you are working through something like this knowing there are people out there willing to help you through it.

---

### Post by BslBryan on 2009-07-19
> **ncumming said:**
> well for anyone out there following this thread i am officially giving up.  just downloaded and ran killdisk at one more (in hindsight futile) effort to try to erase this disk and make it useable again, and even that hangs up.  So its off to the recycling bin for this drive.  Now it seems cheap to pay $80 for a new drive.  I'd pay twice that to get the last week of my life back...

[http://ubuntuforums.org/images/smilies/eusa_wall.gif](http://ubuntuforums.org/images/smilies/eusa_wall.gif)

I also had your problem and when I unplugged the second HD, everything ran smoothly.

---

