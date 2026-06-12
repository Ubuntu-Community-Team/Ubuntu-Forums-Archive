---
title: "Help with recovering deleted NTFS partitions"
date: 2008-11-19
forum: General Help
---

### Post by Hex on 2008-11-19
Yep, I did it, instead of formatting my SD card (using Gparted) I formated my drive. So here's how I goofed up:

1. Deleted all partitions on the NTFS drive (/dev/sda in my case).
2. Converted to fat32 and a single partition of 180gb. (weee!)
3. I keep hitting my head, since all my photos and work was there.

First concern - my PC booted from that drive and GRUB data was written there (although Ubuntu is on /dev/sdb). Will I have problems restarting and booting into Linux?

Secondly, but most importantly, any tips on recovering the partitions or at least the data? I've tried using gpart and it finds my C: drive, but my D: drive is missing (and that's where all the files I need are). Here's what gpart spits out:

```

Begin scan...
Possible partition(DOS FAT), size(190779mb), offset(0mb)
End scan.

Checking partitions...
Partition(DOS or Windows 95 with 32 bit FAT, LBA): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 012(0x0C)(DOS or Windows 95 with 32 bit FAT, LBA)
   size: 190779mb #s(390716802) s(63-390716864)
   chs:  (0/1/1)-(1023/254/63)d (0/1/1)-(24320/254/63)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r


```

Of course, I've refrained from writing to sda, until I get some help from you. Any tips on recovering the data from my D: drive? I don't care that much about restoring the drive, but I need my personal data.

Any help greatly appreciated (in ice-cold beers!).

---

### Post by marshall.robert on 2008-11-19
It is a VERY good idea to refrain from using the drive atall untill you have found somehting that works! there is a good chance that it hasnt actually nuked the data there, but just redone the partition table.

When I ran into a similar problem with deleting an ext3 partition I got pointed to a lot of messy stuff using fdisk.

[http://ubuntuforums.org/showthread.php?t=747260](http://ubuntuforums.org/showthread.php?t=747260) - My thread, if its of any help.

Sorry I cant help you more.

-Rob

---

### Post by prshah on 2008-11-19
> **Hex said:**
> Yep, I did it, instead of formatting my SD card (using Gparted) I formated my drive. So here's how I goofed up:

1. Deleted all partitions on the NTFS drive (/dev/sda in my case).
2. Converted to fat32 and a single partition of 180gb. (weee!)
3. I keep hitting my head, since all my photos and work was there.

Of course, I've refrained from writing to sda, until I get some help from you. Any tips on recovering the data from my D: drive? I don't care that much about restoring the drive, but I need my personal data.

Any help greatly appreciated (in ice-cold beers!).

You can easily recover all your data from the drive. I'd suggest stuffing it into a USB enclosure, then plugging it into a working computer and using testdisk (it's in the repos) and it's companion program "photorec" on it. Testdisk/Photorec are also available on Windows XP, Vista, and on various live CDs.

You will get 100% recovery and easily too, and free even. I know this sounds like an advert but I've been where you are and this did the job great. (Though, in my case, I needed to recover off a 60Gb Sony Camcorder). Being a little geeky, I used the command line version of PhotoRec, but the GUI works just as well (in fact, better).

See enclosed screenshot to give you hope.

---

### Post by Hex on 2008-11-19
@MR, thanks for the info :)

@prshah, just five minutes ago I ended up on [https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition) and decided to give Photorec a try, but still thanks for pointing it out :)

It's recovered some of my files (18,140 files @ 2gb), but then ends with "Segmentation Fault". I suppose I overwrote something while partitioning?

---

### Post by prshah on 2008-11-19
> **Hex said:**
> 
It's recovered some of my files (18,140 files @ 2gb), but then ends with "Segmentation Fault". I suppose I overwrote something while partitioning?

I don't think so; do you have enough disk space on the partition where the recovered files are being stored?

You can also "filter" the extensions that PhotoRec finds; so you can start by first pulling out your jpgs, then mpegs, then docs, etc. It's a long and weary process but definately better than recreating everything (or restoring from backups).

Once you have recovered as many files as possible, run testdisk to bring your HDD back to life.

You should note the important point that photorec loads your HDD as "RO" (Read only) thus preventing further data loss!

---

### Post by Hex on 2008-11-19
Well, I am backing up to another NTFS partition (on the same drive, where Ubuntu is installed), but I doubt that's the problem. And it has 160gb free space, which is enough to retrieve all files. I'll play with filtering and try to back up only the important files.

---

### Post by Hex on 2008-11-19
TestDisk was able to find a backup sector with the partition information and I restored the partitions. Sadly, I can't boot into Windows (corrupt MBR?), but am now copying all the data, in it's original file structure (yay!) to my other drive.

Thank you Ubuntu and TestDrive, and to all who helped, as promised:

[IMG]http://images-cdn01.associatedcontent.com/image/A1388/138817/300_138817.jpg[/IMG]

And I hope to give you the real thing in person :)

---

### Post by Bigneil on 2008-11-19
I have had a nightmare computer day. i have some how minced up one of my hard drives. this thread gives me some hope, my wife wants to kill me because i lost a loads of jpgs and camcorder avi's. ..... or have i?

I had two hard drives one for os and one for storage. my os drive is the minced one. i have started over with the storage drive (fresh installs), and completely removed the os drive from the pc, and put it into an external box. i still cant get it to mount or dismount, and it doesn't show up in 'My computer' in XP. but it did show up on the disk manager as blank non entity.

My whole trouble started when i re-installed my XP on the free space not used by Ubuntu, But lost dual boot (XP only) so i put in my Ubuntu live cd and decided to re-install that too. But the partition manager would not detect the os drive and wanted me to partition and install on the storage drive. I got a bit lost and clicked to use the whole of os drive then cancelled, but i think that this has done the damage???

I hope the program that was mentioned can help:(

---

### Post by Hex on 2008-11-19
Why did you remove your OS drive in the first place?

If you now have Ubuntu on your OS drive, you can install TestDisk and check what's left of the Data drive.

edit: I believe TestDisk is available for Windows too.

---

### Post by prshah on 2008-11-19
> **Bigneil said:**
> 
I hope the program that was mentioned can help:(

Yes, for sure. But always:

a) First use PhotoRec to recover important files, images, videos
b) _Then_ use TestDisk to try to recover the entire hard drive.

The reason being that if you first do testdisk and recover an "older" partition, then all the files will be even less accessible than before. 

PhotoRec / TestDisk are available for Windows XP, Vista, Linux and on a number of live CDs, so you don't need to install anything to use testdisk. A word of caution: _READ_ all that photorec / testdisk tells you; if you don't understand something, just leave it at that point and post details here for confirmation. Don't blindly click or blunder through the procedure.

---

### Post by Marius Derekus on 2008-11-19
> **Bigneil said:**
> I have had a nightmare computer day. i have some how minced up one of my hard drives. this thread gives me some hope, my wife wants to kill me because i lost a loads of jpgs and camcorder avi's. ..... or have i?



I hope the program that was mentioned can help:(

Your wife will never get off your back, will she. :lolflag: 
(No offense or anything, but one can not help but laugh.) 

Btw, i would help if i could, i earnestly would, but i just don't know everything. Hope your issue gets solved (for you and your wife), and i hope you don't get another one.

---

### Post by Bigneil on 2008-11-20
I didn't explain very well,:(

i had xp and hardy dual booting, but when i downloaded SP3 for the xp it went pear shaped. so i thought 'no problem' and simply re-installed xp on to its partition and avoided SP3. Unfortunatly i lost dual booting, so i used the hardy heron live disk to fire up the ubuntu (this is the point at which i should have sought guidance:oops:. 
I couldn't get my Ubuntu back uless i installed it on the storage drive, or used the whole of The OS drive neuking my brand new xp install. I used partition magic in xp to make os into one partition So and moved my most precious files onto OS drive Thinking they would be safe. so i could use storage drive for ubuntu.

I rebooted into ubuntu from the cd, Partition manager would not allow me to partition the storage drive,

:roll: This is where the lunacy starts. i clicked on 'use the whole of os drive option' hoping a further option to partition it would appear but this was not the case i exitted immediatly. and found that i could no longer boot from it, i thought in my misguided wisdom that if i unplugged Storage drive, the ubuntu partitioner would see os and ask me to partition it instead.. NO..so using ubuntu live cd i tried to mount os drive to retrieve the data, but could not mount nor dismount even asking it to force mount in the terminal. The drive was being recognised as a SCMI or SMCI i cant remember. This is where i decided to remove the drive and install it into an external case and plug it into another pc running xp to try and get my info back, but i fialed there too. so i set up my storage drive from the beginning with xp and heron dual boot , NO PROBLEMS.  And put os drive to one side before i do any more dammage.

If you read this far you have earned the right to laugh at me, then get a beer from the fridge,. and use my example as a good reason to regularly back stuff up on to cd's or dvd's

Maybe i should just take the os drive to the computer shop and ask if they can get the info back for me.

---

