---
title: "Reformatting my External HD - Help!"
date: 2006-05-12
forum: Hardware &amp; Laptops
---

### Post by Ruthless on 2006-05-12
I have a HP Pavilion ze4300 laptop (40G) and a Seagate external HD (160G). The external HD has the filesystem of ext3 and I would like to change this all. 

I first want to partition the external HD into 2 different partitions - an ext3 filesystem and a fat32 or ntfs filesystem.

At the current point in time I am making backups of the information contained on the external HD, but will very shortly be ready to make these partition and filesystem changes. 

My question is how do I go about doing all of this? I am using Breezy and am relatively new to linux, so detailed instructions would be very helpful. Also, which filesystem is better for the newly partitioned "windows" section? NTFS or Fat32?

[My reason for all this trouble: I'm going to be duel booting from my laptop, so I would like to still access all my music, pictures, and documents from Windows.]


Thank you,

Ruth

---

### Post by aysiu on 2006-05-12
Is this an external hard drive you'll be sharing with a lot of other computers or just the Windows partition on your computer? Windows can access Ext3 partitions and drives with this:

[http://www.fs-driver.org/](http://www.fs-driver.org/)

Of course, if you plan to use the drive with a lot of different Windows computers, you'd have to install that driver on all of them.

If you decide you want to reformat it, plug the drive in, and in the terminal paste this command: ```
sudo fdisk -l
``` Figure out what its location is. I'm going to guess it's /dev/sda1, but you should check. ```
sudo umount /dev/sda1
sudo apt-get update
sudo apt-get install gparted ntfsprogs
gksudo gparted
``` The rest should be self-explanatory.

---

### Post by Ruthless on 2006-05-12
So I can read ext3 from Windows? Thanks! 

I was going to install Windows on a part of my computer and I wanted to be able to still access my files on the external HD, so if I can just install that driver then I shouldn't have to worry about changing the filesystem of the external HD.

I'll try it out and see if it works.

---

### Post by Ruthless on 2006-05-15
I've run into a major problem. I installed the ext2 thing on a windows computer with my usbdisk attached. When I installed the driver, it gave me the option of naming all the drives on the computer and the usbdisk showed up as all unused space and I could not name it (F:,G:,  etc.). So I umounted it and hooked it back up to my linux computer, only to find that now I can't even recognize the usbdisk! 

I've looked and cannot find it in /etc/mtab and I don't know what to do. I took it over to a Macintosh which recognized it and then said that it was unable to read the file format. 

What should I do?

---

### Post by aysiu on 2006-05-15
Can Windows read it? What file format is your USB disk right now?

Are there important files on it? Have you already formatted it?

---

### Post by Ruthless on 2006-05-15
Windows recognizes that there is a usb device plugged in, but when I go to My Computer, it does not so any extra drives or devices. 

My USB was ext3.

There are important files on it and I have not formatted it yet.

---

### Post by aysiu on 2006-05-15
Can you boot into Ubuntu, plug the drive in, and then paste these commands into the terminal? ```
sudo fdisk -l
cat /etc/fstab
df -h
``` And then can you post the output of those commands back here?

---

### Post by Ruthless on 2006-05-15
First:

```

reh@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        4620    37110118+  83  Linux
/dev/hda2            4621        4864     1959930   82  Linux swap / Solaris

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table 

```

Second:
```

reh@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda        /media/usbdisk  ext3    rw,nosuid,nodev 0       0

```

Third:
```

reh@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1              35G  4.6G   29G  14% /
tmpfs                  94M     0   94M   0% /dev/shm
tmpfs                  94M   13M   81M  14% /lib/modules/2.6.12-10-386/volatile

```

---

### Post by aysiu on 2006-05-15
Yikes! This is bad: ```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

**Disk /dev/sda doesn't contain a valid partition table**
``` Is it possible it didn't get fully formatted in GParted? I'm not sure how to rescue data off a partition table that's not valid. I'm sure it can be done, though.

I'll try to research this with Google, and maybe, in the meantime, someone else more knowledgeable than I can help...

---

### Post by aysiu on 2006-05-15
A quick Google search popped up [this](http://geekblog.oneandoneis2.org/index.php?m=200602): > So, I wanted to edit my grub config to reflect the change from vesafb-tng to vesafb. For reasons my readers might remember, my grub config lives on my IDE hard drive instead of my SATA one. So, mount /dev/hda1 /mnt, I typed, as I have so many times before.

But it locked up.

Odd.

I killed the xterm. A few seconds later, the PC locked up.

That IDE hard disk must be going, I thought. Blast.

Rebooted. GRUB failed to load - no big shock, GRUB lives on IDE. Dusted off my Grub CD, and rebooted. Told it to grab the config file that lives on my SATA disk.

Disk unreadable.

Uh-oh. . .

So out comes the Grub CD, in goes the Knoppix one.

fdisk -l, don't fail me now.

Disk /dev/sda doesn't contain a valid partition table

AAAAAAAGH!

Nooooooo!

My files!

My custom kernel config!

My music collection!

My desktop config!

WHAT HAVE YOU DONE TO ALL MY DATA, YOU BASTARD COMPUTER????

A helpful chap on the Gentoo forums pointed me to a bit of software called testdisk, which I couldn't get on with. But a Google for similar software found me "gpart" - a little utility that scans a hard drive, looking for partitions the hard way, and then giving you the option of writing a new partition table to the disk based on where it thinks the partitions should be.

You have no idea how hard it was to press "Enter"

But I pressed it, and it wrote to the disk.

I still couldn't get back to Gentoo via Grub. But Knoppix could find & read every partition and their contents.

*huge sigh of relief*

At this point, I mounted my SATA root partition at /mnt/sda6, mounted the /boot, /home/ and other partitions in the appropriate place within the mounted / partition, and proceeded to cp -Rav * to my IDE hard drive.

Before doing anything else, I wanted to have everything backed up safely.

Once I had my complete backup, I put my Grub CD back into the drive, booted off it, and manually entered the necessary commands to find & load the kernel.

And here I am, typing this blog entry from my comfy Gentoo install running off my SATA drive.

:o)

I still have to do some fixes - like getting Grub to work from the hard drive - but Hell, that's no real issue. The thing I was really afraid of was loosing all my data.

Thank Root for recovery tools and rescue disks! (God, root, what's the difference? ;o)

Just for good measure, I'm updating my backups on my USB hard drive as well. And I'll look into proper backing up methods when I get a minute.

In the meantime, I shall just enjoy having a working PC for a while :o)  Might that help?

---

### Post by Ruthless on 2006-05-15
I'm googling gpart and I'll play around.

EDIT:

I am looking at the gpart download information ([http://www.stud.uni-hannover.de/user/76201/gpart/#download](http://www.stud.uni-hannover.de/user/76201/gpart/#download)) and am very confused by it all. What exactly do I do to get it working and perhaps find a partition on my drive?

EDIT2:

I downloaded the gpart.linux, ran chmod +x, then ran ./gpart.linux /dev/sda


It's scanning now....

---

### Post by oneandoneis2 on 2006-05-15
Okay, gpart...

Here's how the hard disk works: It has a little table at the very start of the disk, where it records the size & location of all the partitions. Unfortunately (as my quoted blog post mentioned) this table can be lost sometimes, and then your computer doesn't know how many partitions you have or where they are.

However, (usually) if the table is lost, the partitions are still there, on the disk: It's like a book with no Table of Contents.

gpart scans the disk byte-by-byte, painstakingly looking at the whole thing. Unless the partitions have been over-written with new data, it should be able to find all of your partitions, and from that work out what the partition table should say.

If you agree with it, you can then write that new table to the disk by running gpart with the -W switch, and hopefully regain a fully-working disk.

There's no gaurantees, of course, but that's how it's supposed to work. And that's how it DID work when I had to fall back on it.

---

### Post by aysiu on 2006-05-15
oneandoneis2, is that really you? I can't believe you're here helping out. That's cool.

Author of "Linux is not Windows," right?

---

### Post by oneandoneis2 on 2006-05-15
Yah - ruth posted the question on my blog, but I figured it'd be more helpful putting an answer on a forum that people read ;)

---

### Post by Ruthless on 2006-05-15
You guys are so great. Thanks for all your help.

Right now I am still running the gpart cmd and it is Still displaying "Begin scan ..." so I'll post the output when or if it ever finishes.

**EDIT:**

I woke up this morning and came to check on how the gpart "Begin scan ..." was doing.

It Still Just Says "Begin scan..." Do you think it's not working?

---

### Post by oneandoneis2 on 2006-05-16
Afraid not - you should get results within minutes, there's no way it should take days.

---

### Post by Ruthless on 2006-05-16
Perhaps I just didn't install it correctly:

I downloaded gpart.linux  to /home/reh/Desktop.

Then.....

```

cd ~/Desktop
sudo chmod +x gpart.linux
./gpart.linux /dev/sda

```

I tried other variations such as
```

./gpart.linux
gpart -W /dev/sda

```

---

### Post by oneandoneis2 on 2006-05-16
Hmm.. well, I just did the exact same thing & it worked fine.

Maybe try running gpart via sudo? It should give an error message if there's a permissions problem, but you never know..

---

### Post by Ruthless on 2006-05-17
This was the reply I received from Michail Brzitwa concerning the "Begin scan ..." message and the installation troubles.


> 
If gpart says nothing it finds nothing. The most common mistake in
this scenario is that the original disk geometry differs from the
current geometry, i.e. the disk was formatted using a particular
number of cylinders, heads and sectors, and the geometry that is
currently used for the scan (other machine, other disk controller
than before).

So please find out the exact geometry (do a 'dmesg|grep sda' to get
hints), and give gpart the 'verbose' option ('gpart -v /dev/sda')
to find out what geometry gpart is using. Regards,
--
Michail Brzitwa        


---

### Post by oneandoneis2 on 2006-05-17
And what does running gpart with the verbose option give..?

---

### Post by nolongerlivecd on 2006-05-17
Hey, I faced the same problem with my 30GB external HDD, partition table corrupt. I sent it for repairs after 3 months of being unable to FIX the error.

---

### Post by Ruthless on 2006-05-17
When I ran dmesg|grep sda, I received no output but here is the verbose option.


```

reh@ubuntu:~/Desktop$ sudo ./gpart.linux -v /dev/sda

dev(/dev/sda) mss(512) chs(19457/255/63)(LBA) #s(312576705) size(152625mb)

* Warning: strange partition table magic 0x0000.
Primary partition(1)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r
   hex:  00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00


Begin scan...

```

Goodness, I believe I have just lost all the information on the external drive - there goes three years of papers and essays, 35Gs of music, and all my photos and videos. This requires me to say, Bummer.

---

