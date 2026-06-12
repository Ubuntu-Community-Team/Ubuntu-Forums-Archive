---
title: "How do I install a second hard drive (non-dual-boot)?"
date: 2006-05-30
forum: Hardware &amp; Laptops
---

### Post by Pitt Stains on 2006-05-30
Hi,

I've been running Ubuntu for a few weeks, and I need more storage space than I started off with.  I plan to throw another hard drive in the box and set it to slave, but I don't know what to do next.  I'm not trying to do a dual boot thing here, but it will be used exclusively for Windows boxes on the network to store their shared files.

Will Ubuntu automatically detect and install the hard drive on boot?  If so, how do I access it once I'm in?

If not, which is what I suspect, what do I need to do?  I've read a little bit about MAKEDEV, but I'm not sure if this is the right path, and if it is, I'll need a little hand-holding.  I'd like to know what I'm doing before I actually start.

Thanks for your help,
Pitt Stains

---

### Post by aysiu on 2006-05-30
If the drive is not already formatted, you probably want to format it as FAT32.

You can do this using GParted. Just plug the drive in and paste these commands in the terminal ```
sudo aptitude update
sudo aptitude install gparted gksu
gksudo gparted
``` When GParted launches, the initial focus will be on your first hard drive. Click the upper-right-hand corner where it probably will say /dev/hda and select your second hard drive (which will probably be /dev/hdb). Then right-click the partition and select the appropriate option.

Note: in order for GParted to be able to format the new drive, the drive must be plugged in but not in use (it must be "unmounted"). I don't suspect it will be automounted, but you should double-check by typing ```
df -h
``` If you see it mounted, type the appropriate command (I suspect it would be something like ```
sudo umount /dev/hdb1
```

Once you have it formatted, follow these instructions to get it mounted:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by RudolfMDLT on 2006-05-30
[QUOTE=Pitt Stains]Hi,

I've been running Ubuntu for a few weeks, and I need more storage space than I started off with.  I plan to throw another hard drive in the box and set it to slave, but I don't know what to do next.  I'm not trying to do a dual boot thing here, but it will be used exclusively for Windows boxes on the network to store their shared files.

Will Ubuntu automatically detect and install the hard drive on boot?  If so, how do I access it once I'm in?

If not, which is what I suspect, what do I need to do?  I've read a little bit about MAKEDEV, but I'm not sure if this is the right path, and if it is, I'll need a little hand-holding.  I'd like to know what I'm doing before I actually start.

Thanks for your help,
Pitt Stains[/QUOTE]
Hi!

I'm writing an exam tomorrow so I'll get to the point!

If you format the Drive Ext3 - Linux file system, Yes Ubuntu will automatically detect it. If it's NTFS, you will have to mount it yourself and you will not be able to write to it(not an option), If you format it  FAT32 then both Windows & Ubuntu will be able to read and write to it. If the drive is going to be exclusively used by Ubuntu and only networked to by a Windows machine then format it Ext3 because the File system clash between Windows and Linux  is then handled by the Ubuntu machine.

To make life simpler use GParted to do find the drive and partition it. It's a lovely program with a great GUI. To get Gparted, type in the terminal:

sudo apt-get install gparted

So:

1) Connect the drive, making sure that the jumper settings are correct. If the drive is on the same Ribbon cable as you current drive - set it to slave, If it's on the secondary Ribbon you'll have to play around between slave, master and cable select depending on what is already on that ribbon cable.
2) After connecting it up, go to you BIOS and see if your BIOS detects the drive - look if it is listed under the devices that you can boot from.
3)if it is there, boot into Ubuntu and find the drive in Gparted. Gparted can help you partition and mount it where you wish.

For more help on mounting the drive and networking it see this link:
[http://ubuntuguide.org/](http://ubuntuguide.org/)


Cheers and goodluck!

PS: While I was still typing this, it seems aysiu already posted! Sorry to add this... Pitt Stains you'll probaly be better off following the advice of the wise old orange cat!;)

---

### Post by Pitt Stains on 2006-05-31
Thanks, all.  This is very helpful.  I haven't tried it yet, as I'm working two jobs right now and time is tight, but I hope to make time for it tomorrow.  I'll let you know how it works.

BTW, would I have to do things dramatically differently if I decided to use an external hard drive instead of an internal one, or are they treated the same?

-Pitt

---

### Post by aysiu on 2006-05-31
[QUOTE=Pitt Stains]
BTW, would I have to do things dramatically differently if I decided to use an external hard drive instead of an internal one, or are they treated the same?[/QUOTE] For formatting, no. For mounting, they should automount when you plug them in.

---

### Post by Pitt Stains on 2006-06-01
OK, so I decided to go with the external hard drive.  It's a 300 GB.

It's connected and unmounted.  I start GParted, find it (it's called /dev/sda) and there's one NFTS partition on there.  I right click on it and select "Convert to Ext3."  Then I click the "apply" icon to apply the changes.

Next a dialogue box comes up that says "Applying pending operations."  It looks like it's going to load a progress bar but it never does.  It kind of looks frozen (ie, the content of the GParted window behind the dialogue box goes blank), but I can open other applications if I want to.

After looking at that screen for about 45 minutes, I decided it wasn't doing anything, so I tried to cancel, and when that failed, I rebooted the machine.

When I got back into GParted, the partition format was "unknown" (or something like that).  I tried the convert option again, and it's doing the same thing.

Am I doing this wrong?  Should I instead delete the existing partition and create a new one in Ext3 format?  The type of hard drive shouldn't matter, right?  (It's a Maxtor Basic Personal Storage 3200.)

Thanks!

---

### Post by aysiu on 2006-06-01
I think in my original instructions I told you to install *gparted* and *gksu*. If you're dealing with NTFS, too, you may also want to install *ntfsprogs*.

To be honest, though, GParted and QTParted aren't the most reliable partitioning programs around. Unfortunately, they're the only graphical ones for Ubuntu.

I prefer [DiskDrake, but it involves downloading another live CD.](http://www.ubuntuforums.org/showthread.php?t=114142)

---

### Post by Pitt Stains on 2006-06-01
Thanks for your quick response!

I do have gksu installed, but I ran GParted from the desktop (ie, Applications > System Tools > GParted.  I see now in your instructions you run "gksudo gparted" from the command line... I'm not sure if that's the same as using the desktop link.

I don't intend to work with NTFS; that's just the partition that came on the hard drive.

I guess I'll restart the computer again, delete the existing partition, and try to create a new one.  Fingers crossed...

---

### Post by aysiu on 2006-06-01
[QUOTE=Pitt Stains]Thanks for your quick response!

I do have gksu installed, but I ran GParted from the desktop (ie, Applications > System Tools > GParted.  I see now in your instructions you run "gksudo gparted" from the command line... I'm not sure if that's the same as using the desktop link.

I don't intend to work with NTFS; that's just the partition that came on the hard drive.

I guess I'll restart the computer again, delete the existing partition, and try to create a new one.  Fingers crossed...[/QUOTE] Just to clarify:

*gksu* is the package that helps you run it with root privileges. When you use the desktop link, you're using the same command as *gksudo gparted*.

In the original instructions, I did not ask you to install *ntfsprogs* because I didn't know you were getting an NTFS drive. Even if you don't want to use the NTFS drive as NTFS (i.e., you're trying to format it as something else), you'll need *ntfsprogs* to work with it (resize, reformat).

That said, as I stated earlier, GParted and QTParted can just be buggy sometimes. I found it worth it to download the PCLinuxOS live CD just to get DiskDrake--it has never failed me.

---

