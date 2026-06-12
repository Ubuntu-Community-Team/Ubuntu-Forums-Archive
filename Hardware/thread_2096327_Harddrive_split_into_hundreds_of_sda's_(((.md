---
title: "Harddrive split into hundreds of sda's :((("
date: 2012-12-19
forum: Hardware
---

### Post by samtey on 2012-12-19
Hello Ubuntu community!

I'm pretty broke and think about the end of all my files now! :(
A longer time ago, I've installed Ubuntu while I also had 2 Windows 7s on my partitions. I booted my systems always with Grub, as Ubuntu replaced it with my Windows boot managers. Now today, I booted from my Win 7 CD cause I wanted a new OS. When it came to the partition-part, I've formatted my drive where the old Windows was on. I then tried to delete this partition, but it froze for a longer time and I had to reboot my PC. I couldn't boot from any CD anymore (except Ubuntu 10.10) and got the error:

error: no such partition
grub rescue>

I tried repairing / rescueing my Windows with the Ubuntu CD, but when it asked me, which system to root, I saw that my harddisk got split into almost 200 sda's!!! Of course I couldn't figure out anymore what to do, so I had to ask here. I don't wanna lose any of my files, so what now?? :((

---

### Post by Bashing-om on 2012-12-19
samtey; Hi !

Could be a tough call// As you have had windows 7 installed "a longer time ago", I am going to presume the partitioning on the disks are "msdos -> MBR". 

In this situation I would boot up the liveCD, and fire up GParted and get an idea of what exists on the disks and check the outputs of:
```
sudo fdisk -lu
sudo parted -l 
sudo parted /dev/sda unit s print
```Having some idea of the state of things, I would next -in the file manager nautilus- see if all my files were still intact and their locations.

IF windows partitions- use the window's disk utility to delete the extraneous partitions.
IF ubuntu partitions - use GParted to delete those extraneous partitions.

Install winows 7, requiring the (re)installation of grub to the booting hard drive's MBR

Hopefully ubuntu is alive and well and will require no further attention. (fdisk's output will give a strong indication).
[INDENT]just try'n to help <== BDQ

[/INDENT]

---

### Post by oldfred on 2012-12-20
Windows corrupted partition table. 
And then the logical partitions get cross linked and you get the same group of partitions looping and increasing in numbers.

Sometimes this works.

       Your partition table is slightly messed up. But it should be easy to fix. Boot into Ubuntu with Supergrub
sudo fdisk /dev/sda
Press "w". That rewrites the partition table. Reboot (using Supergrub) so that the changes take effect. 

    
       sda60 error:Linked logical partition error
[http://ubuntuforums.org/showthread.php?t=1880513](http://ubuntuforums.org/showthread.php?t=1880513)
[http://ubuntuforums.org/showthread.php?t=1849060&highlight=hundreds+partitions](http://ubuntuforums.org/showthread.php?t=1849060&highlight=hundreds+partitions)

---

### Post by Bashing-om on 2012-12-20
Wow, now that is experience ---talking ! Thanks oldfred.
(made my whole evening worthwhile)

---

### Post by fdrake on 2012-12-20
> **oldfred said:**
> Windows corrupted partition table. 
And then the logical partitions get cross linked and you get the same group of partitions looping and increasing in numbers.

Sometimes this works.

       Your partition table is slightly messed up. But it should be easy to fix. Boot into Ubuntu with Supergrub
sudo fdisk /dev/sda
Press "w". That rewrites the partition table. Reboot (using Supergrub) so that the changes take effect. 

    
       sda60 error:Linked logical partition error
[http://ubuntuforums.org/showthread.php?t=1880513](http://ubuntuforums.org/showthread.php?t=1880513)
[http://ubuntuforums.org/showthread.php?t=1849060&highlight=hundreds+partitions](http://ubuntuforums.org/showthread.php?t=1849060&highlight=hundreds+partitions)


damn... where exactly did you learn so much about partitioning ?? is it just experience or can you give us some resources/books to read. I am very interested to find out since you are the one that is the more informed in the forum about this subject and i'd like to learn tooo :D

---

### Post by oldfred on 2012-12-20
I am retired, like fixing computers (my boss at work had to tell me to stop as I was a manager). So now I have lots of time. 
I have a terrible memory, but excellent recall so I keep notes. And update notes with corrections if the user says something worked or worked better than what I suggested. I often check other threads that I may not have suggested something just to see if someone else suggested something better and often they do. But I do not really know the internal details like a very few here do.
Then I search my notes, but I try to stay with boot & install issues as I do not have good notes on all the other issues as they are changing also. 
The rest is experience or really lots of notes. :)

---

### Post by samtey on 2012-12-21
Hey oldfred, your idea sounds pretty good. I'm gonna try it out as soon as possible! :D There's a question left though (since I'm still very new to Ubuntu): how can I boot with Supergrub?

Thanks for all the answers!

---

### Post by oldfred on 2012-12-21
Supergrub may or may not work. It is a small bootable disk that just looks for other systems to boot. Because of linked list it may take a long time to search or may not work as it cannot stop searching. 
       [http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

    
The links show just running fdisk from your liveCD as another choice. You do have to be sure which drive is the drive with the issue when you boot.

The other possibilities listed in the second link were fixparts and testdisk which both are used to repair partititon issues, but not this one specifically.

But in all cases it would be worthwhile to have a copy of your partition table. If you know start & size if each partition it is possible to restore.

Either post the first part before it loops or run this:
       Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PTsda.txt

---

