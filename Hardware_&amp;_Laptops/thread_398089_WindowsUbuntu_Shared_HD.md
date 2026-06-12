---
title: "Windows/Ubuntu Shared HD?"
date: 2007-03-31
forum: Hardware &amp; Laptops
---

### Post by Puppy fam on 2007-03-31
I just got my new computer (yeah!) which has two hard drives (Ubuntu on one HD and XP on the other). The two hard drives can't share files right now, but I'm wondering if its possible to have a shared 3rd HD? An external USB one maybe?

Thanks!

---

### Post by dfreer on 2007-03-31
Sure it's possible. Format the 3rd Hard Drive with FAT32, which both linux and windows can write to. You can also: 
Shrink the windows/ubuntu partition and create a shared partition on the HD.
Try the NTFS 3g driver to let ubuntu natively write to XP's NTFS partition (not really recommended) Their site: [http://swik.net/ntfs3g](http://swik.net/ntfs3g)
Use a network share

---

### Post by daynah on 2007-03-31
EDIT!!!! After reading dfreer's answer (when I started typing, no one had answered), I'm seriously wondering if I'm understanding what you want to do. If what you want to do is...

You have two hard drives in your computer, hard drive A is Windows, harddrive B is Ubuntu. You would like them to talk. And you also have an external hard drive C that you want to work with both harddrive A and B, then what I'm saying is going to work.

Otherwise, just ignore everything below. and go, "Oh, what a sweet crazy lady."

------(end edit)------

First off, about your current two harddrives. You can get them to talk like such, if your windows happens to be formatted as NTFS.. To check if it's NTFS, type "sudo fdisk -l" If it's NTFS, you're ready to go for this guide, which teaches Linux how to talk to NTFS (internally).

[http://lifehacker.com/software/ubuntu/ubuntu-tip--how-to-mount-a-windows-ntfs-partition-203102.php](http://lifehacker.com/software/ubuntu/ubuntu-tip--how-to-mount-a-windows-ntfs-partition-203102.php)

Now for that external... If there's nothing on the external, go ahead and plug in it while in Ubuntu, install gparted (if in gnome, qtparted I think if it KDE) and format it to NTFS format and follow this guide for the external.

[http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)

NTFS is a nice little way for Linux and Windows to communicate. :)

---

### Post by Puppy fam on 2007-03-31
^ Thanks! It would be ideal for hard drives *a* and *b* to communicate with each other **and **external drive c, but I would settle for just being able for *a *and *b *communicating with c. 

> Now for that external... If there's nothing on the external, go ahead and plug in it while in Ubuntu, install gparted

Would I be installing gparted on the external hard drive or on Ubuntu?

---

### Post by dfreer on 2007-03-31
Well, assuming you have XP formatted with NTFS (default). 

(1) Ubuntu can already read any file on the XP drive, and it can *write* to that drive with NTFS3G installed. But XP will not be able to read OR write to Ubuntu. So all the sharing would have to be done from the Ubuntu end, which isn't so bad. A => B[I]
Cons: Windows will have to host all the shared files, using it's disk space exclusively. Windows will only be able to see what Ubuntu specifically shared in advance.[/I]

(2) You can shrink your XP/Ubuntu Partition by using gparted (Ubuntu & Windows) or Partition Magic (Windows), create a new FAT32 or NTFS partition (let's call it X). and then Ubuntu can read/write to that partition and Windows can read/write to that partition.  A <=> X <=> B
*Cons: Shrinking partitions is always a risk of data corruption/hosing your partition. **[B]BACKUP your data!!**[/B]. You will have to sacrifice disk space in one of your OS for your new partition.*

(3) You can make the External USB Drive Fat32 or NTFS, and have it perform the same way as above solution. A <=> C <=> B 
**EDIT: You could also Combine Solutions 1+3 or 2+3 so that you can do what you want accomplished. C <=> A <=> X <=> B <=> C   or    C <=> A => B <=> C** 
*Cons: You'll have to have that external usb drive plugged in order to use it (not a problem with Desktops, but laptops....). You'll have slower I/O speeds because it's USB after all.*

> Would I be installing gparted on the external hard drive or on Ubuntu?
gparted is installed on the Ubuntu system by:
```
sudo apt-get install gparted
```

It can then be used to format/repartition any Hard Drive Ubuntu can see. You can't really install programs to a Hard Drive, you install it in the OS. The hard drive just holds Data for the program. Plus, you don't want to format a Hard Drive that has the program you are currently running on it :D

---

### Post by Puppy fam on 2007-03-31
> **dfreer said:**
> Well, assuming you have XP formatted with NTFS (default). 

(1) Ubuntu can already read any file on the XP drive, and it can *write* to that drive with NTFS3G installed. But XP will not be able to read OR write to Ubuntu. So all the sharing would have to be done from the Ubuntu end, which isn't so bad. A => B[I]
Cons: Windows will have to host all the shared files, using it's disk space exclusively. Windows will only be able to see what Ubuntu specifically shared in advance.[/I]

How can I access the XP drive? I don't see it under /media. 

Thanks for all the info, if option 1 works, I'd be plenty happy. :-D

---

### Post by Puppy fam on 2007-03-31
Sorry for the double post. 

I've been working on getting Ubuntu to read/write on the XP hard drive, and I'm really not sure where to look for the XP HD. I thought it would be in /media, but I don't see it.

---

### Post by dfreer on 2007-03-31
Well, it depends on how you set up your system. The common place to put mounted drives is in /media, but in all actuality you can mount a drive to pretty much any folder anywhere on your system. What you need to do now is:
Post your /etc/fstab file. This will tell us info about all of the drives currently mounted.
If you have already installed gparted, run that program (either by *sudo gparted* or clicking System > Administration > GNOME Partition Editor. Find out the name of your XP hard drive and the partition number by using the gparted GUI. Here's a quick tutorial on hard drive names if you don't know it already.
 
Hard drives that are correctly detected (mounted or unmounted) should each have a unique name in /dev folder (/dev/hda1, /dev/sdb3 for examples). The **hd**/**sd** refers to the type of drive (hd=IDE and sd=SATA/SCSI), and the letter after refers to which hard drive (Two IDE hard drives would be listed as /dev/hd**a** and /dev/hd**b**). The number following that refers to the partition number (1-4 should be primary or extended partitions, and 5-X should refer to logical partitions in the order that you created them.

Hope this helps!

---

### Post by Puppy fam on 2007-04-01
^ Thanks for the help. 

Last night I went on IRC and got some help; it should be all taken care of now. I am now able to read/write to the Windows SATA drive using NTFS3G.

Thanks for your help, everyone!

---

### Post by Naike on 2007-04-01
Hi guys, I got a little problem too.

I got Ubuntu ad XP on one HD, and ive diveded it like this:

C: 50GT (NTFS)
*: 50GT ext3
E: 150GT (NTFS)

The * is the ubuntu., dunno why it doesnt have a driver letter?

Anyway this is how it is:
[http://img520.imageshack.us/img520/127/abcgo7.jpg](http://img520.imageshack.us/img520/127/abcgo7.jpg)

And I want that the 150GT part is shared for both OS.
So If i mess my windows up i only need to install it again and drivers, but i dont have to rip my music and stuff.
Same on linux.

So is that correct what i have now?

---

### Post by dfreer on 2007-04-01
> Anyway this is how it is:
[http://img520.imageshack.us/img520/127/abcgo7.jpg](http://img520.imageshack.us/img520/127/abcgo7.jpg)

What you have is pretty good. How much RAM do you have? I notice that your swap file is around 6 GBs, the general rule of thumb is to use 1.5 x the amount of RAM you have (although it shouldn't hurt anything to have it that big, it's just taking up space).

> The * is the ubuntu., dunno why it doesnt have a driver letter?
Drive letters is a Windows thing. Ubuntu doesn't refer to partitions as drive letters, it refers to them as a numerical value (see my above post about that). Not only that, but drives are mounted as folders on the / partition, like my external is mounted at /media/usbdrive

So you are doing fine, and keeping all of your important data on a seperate partition is a really good idea. Go ahead and read the above posts on how to install the NTFS3G driver if you want to write directly to the shared NTFS partition, otherwise read up on some of the other options available to you (also in this thread). Let us know if you have any problems!

---

### Post by jjordan on 2007-04-02
What you have will work, I recommend installing ntfs-3g as discussed above.  Why such large areas for windows and Linux?  I run 7GB for each on a laptop and usually 10GB for each on a desktop.  Swap would be fine at 1.5X RAM (even less if you have enough RAM and don't intend to hibernate).  Formatting the large drive as fat32 will make it more reliable but does have some downsides, 2GB max size limit for a file and no security.  NTFS support under Linux is still beta.  There is also a driver to allow XP to access EXT drives.  Overall you have the right idea, keeping data and programs seperated makes sense and has fallen out of favor only because the software companies believe it is too complex for uses.

-j

---

