---
title: "How to make Mac OS formated harddrive writable?"
date: 2006-10-04
forum: Hardware &amp; Laptops
---

### Post by Aleksandersen on 2006-10-04
Hi,

How can I make my Mac OS Formatted external harddrive writrable on my Ubuntu Dapper dekstop?

---

### Post by William the Conquerer on 2006-10-05
you should just need to run the following from a terminal
```
sudo apt-get install hfsplus hfsutils
```

---

### Post by Aleksandersen on 2006-10-05
I did that with the following results:[QUOTE="Terminal"]hfsplus is already the newest version.
hfsutils is already the newest version.[/QUOTE] I am still not able to write to the disk.

---

### Post by William the Conquerer on 2006-10-05
well ok...  so first off, if you go to a terminal and type
```
mount
```
what does it tell you?  For instance I have a thumbdrive and when I type mount I get a bunch of output including:> /dev/sdb1 on /media/THUMBY type vfat (rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8)
most of it looks like mumbo jumbo, BUT if you break it down it makes alot of sense...
**/dev/sdb1** is where the device IS on your system...  it's not mounted, but udev has found the device and you CAN mount it
**/media/THUMBY** is where the deivce is actually mounted...  so if I went to /media/THUMBY in nautilus or something I could see the files contained in my thumb drive
**type vfat** means that the thumb drive is of type fat32 and that is how linux is reading the mass storage device...  
AFTER all that stuff, the text contained in parenthesis is options for this mount...  the important stuff for being able to read and write to the disk is the **rw** meaning it is mounted as read-write

the uid=1000,gid=1000,umask=077 means it is mounted as 
**U**ser**ID** and  **G**roup**ID** 1000 which is my default username the 
**umask=077** means that the user that it is mounted as has full access to it so if I ls the directory this is what it looks like:```
william@shazam:~$ ls -ld /media/THUMBY/
drwx------ 2 william william 4096 1969-12-31 19:00 /media/THUMBY/
```

SOO, after that long introductin into mounting drives in linux...  which is usually completely taken care of by ubuntu tell me what mount says about your external hard drive and my suggestion is if you want a really quick fix just format the hard drive as either ext3 or fat32

---

### Post by Aleksandersen on 2006-10-05
Can Mac OS 10.4.8 "Tiger" read and write to Ext 3 disks?

If so I will format the drive and do it that way.

---

### Post by William the Conquerer on 2006-10-08
I really don't see why you wouldn't be able to mount it in os x, but I can't give you a definite answer because I don't use os x...  BUT, I did uncover this howto about mounting an HFS+ formatted (OS X default filesystem) in ubuntu

[http://jclark.org/weblog/Miscellany/ubuntumount.html](http://jclark.org/weblog/Miscellany/ubuntumount.html)

---

### Post by Aleksandersen on 2006-10-08
OK, that was a little too advanced for me. And that is how to read from a built in HFS+ disk when using a Macintosh.

I am on a regular PC running Ubuntu, but would like to read and write to a USB hard drive fromatted with HFS+.

And I ran into another problem. I partitioned a small portion of my external USB hard drive to FAT-32 so it could work as a small bridge between my Mac and PC. But after I have written around 50 MBs to it (this varies) I get an error message saying something like "O/I error" and the drive gets unmounted. What causes this? And is there really any reason why I should be bothering with making the HFS+ partition on the disk writable if I am unable to write to it due to some O/I error (which I do not know what is or what is causing it to happen)?

---

### Post by William the Conquerer on 2006-10-09
well let's see...

I kinda wish someone with more experience would post a solution cause I don't really have direct experience with all this...  BUT, this is what I think.

I/O errors are *BAD* there's a chance that means the hard drive is corrupted...  that could be a physical corruption which would mean you might as well start looking into what kind of warranty you have on it...  cause you can't really FIX a physical problem, just kinda delay total failure...  I'm not trying to scare you, but I'm just sayin' this has happened to me and hard drives DO wear out, if your hard drive is less than 2 years old I doubt this is the case though...

Well... ok, so I've got another idea.  If you're not opposed to formatting the whole drive, you could really easily just install gparted ```
$ sudo aptitude install gparted
``` and run gparted as root to format your external hard drive completely as Fat32 ```
$ sudo gparted
```

Ya see...  all three OSs have to be able to read and write to FAT32 cause pretty much all external hard drives and thumb drives have to come formatted as fat32 to be compliant with windows.  I used to do this when I ran a dualboot of windows xp and linux, I kept all my e-mails (using thunderbird), music, and movies on an external hard drive and I could access it from both OSs...  You just can't have any files larger than 4.2 gigs on the drive...

anyway, tell me what you think.

---

### Post by Aleksandersen on 2006-10-10
I did not think that anyone would recommend using FAT as, if I remember correctly, it is a really slow file system.

I have also read that Mac OS 10.4's Spotlight meta and content search might have problems indexing FAT hard drives *(mainly due to slow respond time from the disks or something)*.

And regarding the O/I error: The hard drive is four or five months old. It has almost not been used as it has primarily only been a back up disk. And I never had problems with it in Mac OS.

---

### Post by Aleksandersen on 2006-10-10
So I am stuck with a FAT32 hard drive then. 8-[ Well, I will just have to learn to live with it.

And I hope someone will invent a file system that actually works for everyone soon! I have looked at [Wikipedia's file system comparison chart](http://en.wikipedia.org/wiki/Comparison_of_file_systems) and I cannot say I am all that impressed with support for the various file systems...

It seams like a company just releases a new file system and says "Hey! Look at us! We got a new file system! And you cannot use it unless you are using this very specific operating system. And we do not plan to support other operating systems! Ooo... We are sooo cool!"

---

### Post by William the Conquerer on 2006-10-11
sorry I can't really give a better solution.  I don't really notice slow response times in FAT32...  it's just a fairly primitive filesystem WHICH of course is why it will work for you in all three OSs...  there's been plenty of time and need to build in support for it.  The major filesystems used are FAT32, NTFS, HFS+, and ext3...  corresponding to windows, windows, mac, and linux respectively.  There's a posibility NTFS would work in this situation, simply due to the fact that a read/write method was recently developed for it in linux, not sure about it's status in os x...  Just try fat32, hopefully it plays well with all the OSs, and good luck =).

---

### Post by mssever on 2006-10-12
> **William the Conquerer said:**
> I really don't see why you wouldn't be able to mount it in os x, but I can't give you a definite answer because I don't use os x...  BUT, I did uncover this howto about mounting an HFS+ formatted (OS X default filesystem) in ubuntu

[http://jclark.org/weblog/Miscellany/ubuntumount.html](http://jclark.org/weblog/Miscellany/ubuntumount.html)

This link SHOULD work even with removable disks. What you need to do differently is to look in /dev/disks/by-id with the drive plugged in. You should see one or more symlinks related to your drive. Run parted or GParted on the drive to determine which partition you want. I recommend GParted, where you can select the proper disk from a drop-down menu. Its name will probably begin with /dev/s. Once you find the partition number, notice the proper symlink in /dev/disks/by-id.

Insert the following line into /etc/fstab, using the proper filename (including partition number) for your device:
```
/dev/disks/by-id/ata-IC25N060ATMR04-0_MRG31WK3HBRW8H-part1 /media/macdisk    hfsplus  defaults,sync,rw,noauto   0 1
```It should work now. Note that I'm not a Mac or HFS user, so I can't test this; I'm just applying my Linux knowledge.

---

### Post by Aleksandersen on 2006-10-12
I will just use the FAT32 file format. Really, it is not worth having an Mac OS formatted disk when it is going to be this much trouble,,,

:-|

---

