---
title: "Hard-disk and filing system woes. Testdisk making worse?"
date: 2010-05-15
forum: Hardware
---

### Post by DiegoDeEscocia on 2010-05-15
Please forgive the lenght of the explanation! This has got me at wits end....

Hey all,

I've had a nightmare of a time lately - first my TB backup drive was destroyed in the middle of trying to backup files to install a newer version of ubuntu - I'd resized it as the old version I was installing couldn't write to NTFS.....Testdisk failed to recover it though I wasn't tremendously sure what I was doing.

Then I removed the files to another part of my main computer on a FAT32 partition I'd forgotton I had....

Then all three other OS's started acting up - blue screens galore.

The result is I don't have backups of precious information.

Finally it reached the point that I couldn't boot either Ubuntu or either of my XP installs.

I created a multiple boot from iso usb pen which included AVG's recovery iso.......And one of the tools in this was TestDisk.

First I searched and made a backup. All fine and well although I didn't see my final FAT partition.

I then set TestDisk to search.

It still didn't find it.

I hit deeper search........and it took quite some time.....


and then sucess the last partition on the drive appeared.


I hit the button to show me the files. Then the button to hide deleted, then I switched them on again.....finally I hit the arrow keys on autopilot.....

I tried to exit the file preview.....which I did.

I tried to write the changes.....


Write error.


And now I'm getting read errors on the whole partition table. I can't restore the backup copy I took earlier as it simply gives me 'write error'

Analysisng the disk is proceeding far too fast completing in seconds and giving read errors........

Help! It seems I can't even restore the original partition table....I suspect that as I've loaded Testdisk via an  ISO (using this method:  [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/) )

My partition table backup might be stored in memory and might not survive a restart or even quiting the program.

Anyone any idea what's going on and how to fix it? There are photos of great sentimental importance to me on this drive - not to mention documents essential to my degree.

---

### Post by tgalati4 on 2010-05-15
Get an external drive (USB, flash, anything with enough space to recover your files).

Boot a recent Ubuntu Live CD.


Open a terminal
sudo apt-get install testdisk
man photorec

photorec is part of testdisk.  You were trying to restore a mangled partition table.  Let's try to grab the data first, then you can go back and try to recover the partition table.

Mount your external drive.  Click on it in nautilus and it should mount automatically.  Make a directory to receive any files that photorec picks up.
Let's call that directory /media/sde1/trying_to_recover_my_data

photorec /log /d /media/sde1/trying_to_recover_my_data /dev/sda1

Photorec ignores the partition table and actually looks at the data in the sectors and follows the sector chains for each complete file.  It can pull out most types of media files.

Once you have recovered most of your data, then you can attempt to rewrite your partition table.

---

### Post by DiegoDeEscocia on 2010-05-15
Thanks for your advice. :-)

Is it safe to quit testdisk? I think I may lose the backup file I made as it may only be stored in the RAM....and the changes it seems to have made that resulted in the write errors seem likely to be permenant?....

I'll leave the computer on overnight and check what your council is first thing in the morning as I'm so knackered that my concentration is starting to go :-/

---

### Post by tgalati4 on 2010-05-15
Testdisk just tries to recreate the partition table and file allocation table based on reading the first few cylinders of the disk.  The write errors could be simply that you didn't use:

sudo testdisk /log /dev/sda1

Linux mounts bad disks as read-only to prevent further damage.  So without sudo no changes will take place.

I would do the following:

1.) Create a credible data recovery plan and post it for review.

Get another drive (1 TB external USB drive for instance).  Don't mess around with moving data to another partition or rely on smaller disks than the amount of data that you have. You need the space to perform an adequate recovery. 

Make a priority list of your data that you need to recover and focus on that. 

Use a Live CD, install testdisk (it will be installed in RAM) and run photorec pointing to your external drive.

2.)  Execute the recovery and verify that the files you have identified in (1) have been successfully found and recovered.

3.)  Run gparted on the drive to read and recreate the partition table.

sudo gparted /dev/sda

If gparted has problems reading the partition, then go ahead and create new partitions based on your best estimate of how the disk was partitioned.  Write the new paritions to disk.  This can destroy data if your partition guess is widely off of how the disk was originally partition.

This is an unorthodox method of fixing the partition table, but I have used it successfully in the past.  I don't know if it is better than testdisk or not.  If you don't remember how you partitioned the drive, then maybe testdisk is a better tool for recreating the partition table.

4.)  Run fsck on the drive to see how badly it is mangled.

sudo fsck /dev/sda1
sudo fsck /dev/sda2
sudo fsck /dev/sda3
.
.
.
Don't need to check swap.

If you had a simple disk hiccup during your backup, then you can simply do an fsck from the live cd and that will normally fix things.  BUT, if the drive is failing (which is what caused the hiccup in the first place), then fsck can really mess up a drive by trying to fix file pointers with degrading hardware.

The better course is to grab as much data as possible before the drive fails, then if you are lucky to retrieve all/most of your files, then you can proceed to repair the disk with fsck.

What was the initial hiccup that happened during backup?

---

### Post by DiegoDeEscocia on 2010-05-16
Ok the background you requested is as follows. It will be clear that this hasn't been my week with partition tables....I've lost two, one on my backup drive (which you have suggested I might need to resurrect first) and also now my main hard-disk!

The original thing that went wrong affected the windows boot sequence.

I had to go through and reinstall ubuntu...

But of course had important files on linux - hence I wanted to put them on my terrabite drive....but due to some problems I still can't fathom with booting a recent ubuntu live CD I used an old 6.04 LTS.....My terrabite drive was in NTFS and 6.04 LTS couldn't write to that so I used gparted to try to repartition my external drive.

the umount command didn't manage to unmount the drive but I simply ejected it which umounted it and allowed gparted to write to it...

I set it to resize the NTFS partition to free up 6 GB at the end for my linux drive backup and create another partition on the end that ubuntu could write to.

Unfortunately midway through the process of doing this ubuntu auto-re-mounted the terrabite drive (when it suddenly appeared as two new drives).....which interfered with the process somehow resulting in two partitions of 'unknown' file type ('desconocido' - it was running in spanish)......

There went all of my backups from all of my devices!

I solved the problem of the now unbackupable linux partition by putting most of the important contacts on a separate FAT partition I'd forgotten about on my main computer.

I wonder if this could have corrupted anything?

Anyway I downloaded and installed ubuntu 10.04 LTS and suddenly the windows boot sequence appeared again. Windows prompted to check/repair the main hard-disk....I let it do it (I can't remember the exact text).....

It went through a rather lenghty process then bluescreened and rebooted. Windows was unbootable.

Ubuntu hung on boot on the loading screen and the first time showed something about being unable to mount sda2 or something similar....

With no OS now bootable I created the bootable USB pen with AVG's recovery ISO and booted to it........

So test-disk is running from AVG recovery presently not your regular Live CD.......

Furthermore I succeeded in searching for and finding my newly missing fat partition in the first instance without read errors....

Furthermore I also managed to perform a backup of the partition structure before doing it......

However after looking at the files to check they were all there - which they all were  - I went back somehow to the main menu and now all I'm getting are write errors and I can't even restore the original backup of the partition structure :-/

To follow you're instructions I think I will first need to quit testdisk on the live CD thus losing the partition table backup for how things were at the start of the procedure....but I think there's no way to get round the write errors anyway.....


Problem summery:

1. If I quit I'll lose the backup from testdisk I *think*....Any way to save it so that it's still there for the worstcase scenario?

2. The only disk I had big enough for the process is my TB disk which was unfortunately destroyed in the auto-remount incident....and indeed I'd hoped to attempt to recover afterwards.......Might hopefully be as simple as writing NTFS to the entire partition size for that one?


Presumed action plan:

(1)
Quit testdisk, sacraficing the backup copy.....Might take a photo of the screen so that worstcase I could try manually typing in the arrangement later?

(2) boot into a ubuntu liveCD....

Rewrite the nfts fileing system on my terrabite external drive which used to only have *one* partition on it which was NTFS taking up the entire drive, It had 300GB odd of data on it and I have no drive big enough to attempt to use photorec with it....? So how do I do that trick you suggested with guessing the sizes?....Hopefully this will undo the repartition damaging from before and give me my files back?

If that fails throw away the chance of recovering the 300GB of data and repartition the drive accepting the loss of the 300GB of old files. Then attempt file recovery for the main hard-disk using Photorec and the newly repartitioned TB drive as a target.

---

### Post by tgalati4 on 2010-05-16
Well, it sounds like you went through quite a struggle.  In the future, a flubbed boot can sometimes be fixed using a recent Ubuntu Live CD:

sudo update-grub

It will search your disks for operating systems and then ask if you want to include them in your boot list, then rewrite the Master Boot Record (MBR).  This will often fixed a borked MBR which sometimes happens when you have Windows anywhere near your computer.

I don't know if testdisk will properly save your previous configuration.  If it is seriously borked then it won't be able to rescue it anyway.  Yes, Dapper Drake did not have NTFS write support.  As I recall, there were some bugs/stability issues so it was not included by default.  You can download ntfs support under Dapper, but you really need a newer Live CD to do this kind of work.

Taking a picture of the screen would be helpful to capture the existing disk arrangement.

Get a newer Live CD (Harder or newer).

For the TB external drive, if the repartition was successful, then your data will simply be moved to the squished NTFS partition.  If you don't remember the exact size of each partition (# of blocks), then try running testdisk on the external drive using the Live CD and testdisk should be able to recover the partitions.  Otherwise, if these photos are important, go out an purchase YATBD.

With a fresh drive, format it with FAT32 (unless any single file is greater than 2 GB) or ext3 using gparted.  Once the drive is formated you have to add a file system to it:  (Presuming you have two 500 GB partitions on your new TB drive.)

sudo mkfs /dev/sdf1
sudo mkfs /dev/sdf2

sudo mkdir /media/recovery
sudo mount /dev/sdf1 /media/recovery
sudo mkdir /media/recovery/photorec_recovery_16_May_10

sudo photorec /d /media/recovery/photorec_recovery_16_May_10 /dev/sde1

Use the Live CD and run gparted on the internal boot drive and report back what it says.

sudo gparted

---

### Post by DiegoDeEscocia on 2010-05-17
Thanks so much for all of your help!

I actually originally tried the grub-update method. It failed to recover the problems. I was about to try loading a windows recovery CD and running fixmbr too when I just decided that my ubuntu install needed upgrading so a reinstall would be welcome anyway.........Hence the mess I've ended up in!

One last tiny piece of detail about the process you described for recovering the data on the TB drive - which I'm keen to do if possible before continuing - by repartitioning it.

The stage at which the Gparted remounted it might be inferrable from the fact that afterwards the partitions of the external drive  had the following characteristics:

1. Unknown filing system
2. The first partition, formally the main NTFS one, contained all the space The second one appeared there but not to contain any space whatsoever on Gparted.....

Would it be a good supposition that the process was interupted at a very early stage and that likely only the entry for the ext3 partition had been created.....i.e. if the whole thing were turned into a single NTFS partition in the first place the problem would be reversed?


And the really important thing:

How do I go about doing as you said - creating the partition that was deleted but **without** reformatting it and thus losing the structure of the previous partition? Did you say I could do that with gparted?

PS -successfully got Linux Mint 8 - which is really just a skinned version of a later Ubuntu version running. I'm using the live CD to type this to you now!... I took a photograph of the main HD.

Also significant was that on booting up Mint I was greeted with a message that said 'One or more disks are failing'  and a warning reading "Disk has many bad sectors"....

I took a photograph of the screen with the old partition table sizes for use later on as you suggested :-)

Looks like next step is to recover the terrabite drive....but how?

---

### Post by tgalati4 on 2010-05-18
gparted does not format drives unless you tell it to.  Rewriting the partition table does just that.  The data is still there, but the OS needs a valid partition table to find it.

When you right click on a partition in gparted, you have the option to format it, but don't do that.  You also have the option to check it--which you should.  You can also see the detailed information about the partition.

If you are confident that the entire drive is one big ntfs partition, then delete all of the partions and create one new partition as ntfs, but don't format it.  Formating occurs after the partition table is created.  When you have made the changes to reflect your best guess as to how the drive was originally structured, then hit the "apply" button and the new table will overwrite the old table.

Then close gparted and run it again:

sudo gparted /dev/sde           (or whatever your external drive is called)

It will scan the partition and hopefully it will stick.  If the drive is damaged in the first few cylinders where the partition table is stored, then gparted will tell you that you don't have a valid partition table.  If gparted can't write a valid partition table, then the drive can't be used.  You may be able to recover the data with photorec as I have described above, but you won't be able to use it anymore.  Sometimes you can run a "low-level" factory format using the manufacturer's utility to restore a drive.  I've had 50% success with such formats reviving drives.

You can also use badblocks to scan the entire drive for a list of bad blocks and then use fsck with the -cc switch to mark them as bad.  This is only practical if there are only a handful of bad sectors.  If there are too many, then the location table gets full and that can cause extreme pain.

Once you have written a valid partition table then run an fsck on it but don't fix the errors, just page through them to see how many there are.  If there are only a few, then run the check again and fix them.  If there are hundreds, then you have bigger problems.  Run photorec to recover any data before allowing fsck to fix errors.  Hundreds of errors could indicate a disk crash, or a malformed partition--the data on the drive does not conform to the partition table.

I like Mint8.  I've been running it on my thinkpad for the past year.  It's pretty solid.

---

### Post by DiegoDeEscocia on 2010-05-18
Ok - progress! I successfully recreated an ntfs partition on the Terrabite backup drive using gparted by:

deleting both partitions.

Create New partition > Whole disk space and filesystem type NTFS  and re-entering the old volume name 'Expansion Drive'

On creation the new partition the terrabite drive is now mountable again.....


*but* appears not to have any files on it....... :-/

Anything I can do to attempt to make the files on it re-appear before I use it to backup the laptop's hard-disk?

There are files that are 7 or 8 GB in size on this drive.....

Thanks again for all of your advice! I appreciate I'm taking this recovery very very slowly but I don't want to take any guesses and spoil any chances at saving this stuff!

---

### Post by tgalati4 on 2010-05-18
Did you run photorec on the drive?  The file system has no pointers to where the files are on the disk but the data should still be there.

Since you now have a recognizable partition table on the drive, you can also try to run testdisk and repopulate the filesystem on that partition, but I would focus on recovering the data first with photorec first.

---

### Post by DiegoDeEscocia on 2010-05-19
Ah I see, I don't have a drive bigger than the TB one for the restore {or even a second TB Drive)........So will I need to repartition the last half of it - which had no data on it before hand - and use that for the process? I seem to remember you saying that wasn't a good idea when talking about the main HD.....

Is this going to need me to shell out on a second TB HD to save my backup drive files? :-/


As soon as I've attempted to retrieve the files on the TB drive I'll press ahead with trying to recover the main HD using photorec as per your instructions :-) Just don't want to lose the chance of recovering my backup drive first!

---

### Post by tgalati4 on 2010-05-19
I seem to recall writing:

Otherwise, if these photos are important, go out an purchase YATBD.

Yet Another Terabyte Drive.

You can't rely on existing drives to provide backup capability because each one of them is suspect in terms of valid MBR, partition tables, etc.

Only a fresh drive, with a fresh partition table, and no history of being messed up is called for in this situation.

Regarding not finding your files after making a new partition table:

When you make a new partition table, say one large NTFS partition on the drive, the next step is to put a file system on it:

sudo mkfs /dev/sda1

That will reformat your drive (based on the partition label--NTFS in this case) and surely wipe out any data remaining on the disk.

You DON'T want to do this.

What you DO want is to allow linux to be able to mount the drive and you need a valid partition table to do that.  Once the drive is mounted then you can start to use recovery tools such as testdisk and photorec.  Photorec is called for in this case because you want to recover data.  You don't really care about recovering the file/directory structure and using the disk again as if nothing happened.  

This concept of separation of partition table from formatting partitions with file systems is completely foreign to Windows users.

Good luck in your recovery.

---

