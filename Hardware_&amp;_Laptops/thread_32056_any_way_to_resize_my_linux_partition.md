---
title: "any way to resize my linux partition?"
date: 2005-05-05
forum: Hardware &amp; Laptops
---

### Post by simianMiscreant on 2005-05-05
I want 5-10gb for Windows Longhorn, and I'd rather take it out of my 35gb Linux partition than my 55gb Windows XP partition. PartitionMagic 8.0 (a Windows app for partitioning) won't TOUCH my Linux partitions, so i was hoping you all knew how i could resize my Ubuntu partition (maybe something clever with the utils on the Ubuntu Install CD?). Thanks in advance, guys!

---

### Post by jodef on 2005-05-05
> I want 5-10gb for Windows Longhorn, and I'd rather take it out of my 35gb Linux partition than my 55gb Windows XP partition. PartitionMagic 8.0 (a Windows app for partitioning) won't TOUCH my Linux partitions, so i was hoping you all knew how i could resize my Ubuntu partition (maybe something clever with the utils on the Ubuntu Install CD?). Thanks in advance, guys! Don't use PartitionMagic on Linux machine unless you want major headaches. You might be looking for something like [Gparted](http://gparted.sourceforge.net/)

---

### Post by Xian on 2005-05-05
[QUOTE=simianMiscreant]PartitionMagic 8.0 (a Windows app for partitioning) won't TOUCH my Linux partitions, so i was hoping you all knew how i could resize my Ubuntu partition (maybe something clever with the utils on the Ubuntu Install CD?).[/QUOTE]
You basically have to be mildly nuts to try and resize a Linux partition. There are methods which are done via the command line which can attempt such a procedure, but they are intricate and require some advanced skills. The GUI methods are totally unreliable. I personally would not try it as I've seen many a partition burned due to this.

---

### Post by Seth on 2005-05-06
[QUOTE=Xian]You basically have to be mildly nuts to try and resize a Linux partition. There are methods which are done via the command line which can attempt such a procedure, but they are intricate and require some advanced skills. The GUI methods are totally unreliable. I personally would not try it as I've seen many a partition burned due to this.[/QUOTE]
 Hi. I'm Seth. I just resized my ext3 partition a few days ago. Using PartitionMagic. In Windows. I took 10GB from an NTFS partition, and gave it to the ext3 partition. It was painless. I'm still here.

:-p

---

### Post by Xian on 2005-05-06
[QUOTE=Seth]Hi. I'm Seth. I just resized my ext3 partition a few days ago. Using PartitionMagic. In Windows. I took 10GB from an NTFS partition, and gave it to the ext3 partition. It was painless. I'm still here.[/QUOTE]
I don't use Windows but good to hear you had success.

---

### Post by jodef on 2005-05-06
[QUOTE=Seth]Hi. I'm Seth. I just resized my ext3 partition a few days ago. Using PartitionMagic. In Windows. I took 10GB from an NTFS partition, and gave it to the ext3 partition. It was painless. I'm still here.

:-p[/QUOTE]PartitionMagic is ok for resizing windows partitions but just browsing a few linux forums will tell you generally PartitionMagic and Linux don't seem to be a good combination. Don't use it to resize your linux partitions. I can't tell you the number of times people have used PM and then realized they couldn't boot linux.
> You basically have to be mildly nuts to try and resize a Linux partition. There are methods which are done via the command line which can attempt such a procedure, but they are intricate and require some advanced skills. The GUI methods are totally unreliable. I personally would not try it as I've seen many a partition burned due to this. Maybe a while back this was true but I have used tools like diskdrake and qtparted and a few others and have never had problems resizing Linux (Ext2,Ext3 and Reiserfs),Windows (FAT and NTFS) partitions. And I have literally resized about 50 or 60 different partitions. The thing is that DATA LOSS can occur doing almost anything on a computer so always backup. That said resizing in linux today graphical or not, not any riskier than any other operation.

---

### Post by az on 2005-05-06
[QUOTE=simianMiscreant]I want 5-10gb for Windows Longhorn, and I'd rather take it out of my 35gb Linux partition than my 55gb Windows XP partition. PartitionMagic 8.0 (a Windows app for partitioning) won't TOUCH my Linux partitions, so i was hoping you all knew how i could resize my Ubuntu partition (maybe something clever with the utils on the Ubuntu Install CD?). Thanks in advance, guys![/QUOTE]


It is perfectly safe to resize any linux partition using parted.

All the linux partition programs (qtparted, gparted as well as the ubuntu installer) use parted.

Just boot the installer and make your way to the partitionner.  Select maual partitioning and then find your linux partition.  Change it.  Make it's size smaller.

Parted will tell you if this is possibe and move data around for you if need be.  Once it is done, you will see free space available.  Quit there.

Resizing linux ext3 partitions is _very_ safe.  That would not stop me from backing up my data, though.

If you want to use any other tools to resize, you need to boot from another drive or a live cd.  The drive in question must be unmounted while you work on it.  That is why you should not use Gparted or Qtparted from within your current installation.

---

### Post by Rodrigo on 2005-05-06
Partition Magic always Fu** up my Linux partition. In my own experience: use partition magic to resize, move, burn, etc FAT32 and NTFS (and change its cluster size!), and better use gparted in ext2 ext3 and raiserFS. good luck  :grin:

---

### Post by rickwood on 2005-05-06
I resized a linux partition (ReiserFS) a few weeks ago just fine.  I booted using Mandrake 10.1 OE disk 1, clicked yes a few times until it came to partitioning.  I then used Mandrake's partitioning tool to resize the linux partition.  After resizing, I quit the installer.  No problems at all.

I have had problems with Partition Magic in the past, but haven't used  the versions out the last few years.  I've also had problems with QTParted (I believe this is what comes with knoppix) and rendered my system un-bootable.

I've used Mandrake's tool 3-4 times now, and not had any problems.  I have observed, however, that it doesn't seem to want me to move the start of the partition.  But it will let me easily add space to the end of partition.  I haven't tried shrinking a linux partition, but don't know why it would be any different.

---

### Post by Xian on 2005-05-06
[QUOTE=rickwood]I resized a linux partition (ReiserFS) a few weeks ago just fine.  I booted using Mandrake 10.1 OE disk 1, clicked yes a few times until it came to partitioning.  I then used Mandrake's partitioning tool to resize the linux partition.  After resizing, I quit the installer.  No problems at all.

I have had problems with Partition Magic in the past, but haven't used  the versions out the last few years.  I've also had problems with QTParted (I believe this is what comes with knoppix) and rendered my system un-bootable.[/QUOTE]
I've also had success and failures with parted. You can find people who seem to find it always works for them and others that find the entire partition scheme gets hosed. I generally discourage people from doing resizing in Linux, and experience has certainly told me that it is not to the point of being "perfectly safe".

---

### Post by jodef on 2005-05-06
[QUOTE=Xian]I've also had success and failures with parted. You can find people who seem to find it always works for them and others that find the entire partition scheme gets hosed. I generally discourage people from doing resizing in Linux, and experience has certainly told me that it is not to the point of being "perfectly safe".[/QUOTE]I believe that is true in windows as well. Interfering with partition scheme always involves a degree of risk hence only do it once you have backed up your data. Fortunately for me it's one of the areas that has always worked w/out problems :)

---

### Post by az on 2005-05-06
[QUOTE=Xian]I've also had success and failures with parted. You can find people who seem to find it always works for them and others that find the entire partition scheme gets hosed. I generally discourage people from doing resizing in Linux, and experience has certainly told me that it is not to the point of being "perfectly safe".[/QUOTE]


99.999+ percent of people who resize a windows partition to install linux do not have any problems.  All of the distributions I can think of use parted.

---

### Post by Xian on 2005-05-06
[QUOTE=azz]99.999+ percent of people who resize a windows partition to install linux do not have any problems.  All of the distributions I can think of use parted.[/QUOTE]
Nah, I was referring to resizing Linux partitions. 
The FAT and NTFS filesystems are generally not a problem.

---

### Post by Rehevkor on 2005-05-08
I have been trying very hard for a couple days now to resize an ext3 partition, and have had no success. qtparted, parted, and gparted all refused to even allow me to resize it. I used tune2fs to remove the journal and tried again, and got "filesystem has incompatible feature enabled" when trying to resize it. I hate obfuscated error messages >_< WHAT feature?

I even tried doing tune2fs, then use resize2fs to resize the filesystem, and THEN using parted to resize the partition, and still got that error. I also tried using the partition interface in the Ubuntu installer, and it flat out told me "it is impossible to resize this partition."

I've come to the same conclusion, so I'm going to delete the bastard and start over. I just hope I don't have to resize again any time soon.

---

### Post by telmo on 2005-05-08
Just a quick note...:

NEVER use Partition Magic!!! Use Acronis Partition Expert instead!

I'm saying this because i screwed my hdd so many times with Part. Magic and not even once with Part. Expert.
(not advertising, i promiss!)

---

### Post by jodef on 2005-05-08
[QUOTE=Rehevkor]I have been trying very hard for a couple days now to resize an ext3 partition, and have had no success. qtparted, parted, and gparted all refused to even allow me to resize it. I used tune2fs to remove the journal and tried again, and got "filesystem has incompatible feature enabled" when trying to resize it. I hate obfuscated error messages >_< WHAT feature?

I even tried doing tune2fs, then use resize2fs to resize the filesystem, and THEN using parted to resize the partition, and still got that error. I also tried using the partition interface in the Ubuntu installer, and it flat out told me "it is impossible to resize this partition."

I've come to the same conclusion, so I'm going to delete the bastard and start over. I just hope I don't have to resize again any time soon.[/QUOTE]Were you trying to resize a mounted partition by chance?

---

### Post by az on 2005-05-09
Exactly!  You need to be running from a live cd (Knoppix, Ubuntu live or even the ubuntu installer...) to resize your disk's partitions.

---

### Post by Rehevkor on 2005-05-10
[QUOTE=jodef]Were you trying to resize a mounted partition by chance?[/QUOTE]
 I was running from a Knoppix cd, and the partition was not mounted. I checked it half a dozen times, and even hit it with umount just in case.

I was only able to accomplish my goal by making a Ghost image of the partition, deleting all partitions, rebuilding them with the correct sizes, and then restoring the Ghost image. Due to the size difference, I also had to run e2fsck and resize2fs on the restored Ubuntu partition to make the added space available.

No matter what I tried I could *never* actually resize an ext3 partition, even if I removed the journal first. One thread I encountered in my research mentioned that some distributions made their own changes to the file system layout. Perhaps that might explain the "incompatible feature".

---

### Post by condorloco on 2005-07-30
I have the same problem. I tried resizing my ext3 partition with gparted and it just doesn't work.

---

### Post by eivind on 2005-08-28
Yep. I have experienced the same thing, booting into Damn Small Linux (version 1.2), and trying to resize the two ext3 partitions on my laptop (40 GB drive). I was not allowed to resize using gparted and qtparted, and I didn't dare to use Parted (too many numbers).

Perhaps I should try Azz' suggestion to use the Ubuntu install CD? But alas, so far, the live cd's I've tried have been to little avail.

---

