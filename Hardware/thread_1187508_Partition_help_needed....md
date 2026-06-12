---
title: "Partition help needed..."
date: 2009-06-14
forum: Hardware
---

### Post by CrimsonEclipse on 2009-06-14
I'm trying to install 9.04 on a disk with XP3 already.
It's a HP DV1000.

The 9.04 has a disk partition that has:
XP
The back up section (likely an image of XP)

Using the 9.04 partition, it tries to make extra space for 9.04 but I get a general error message. 

Should I use partition magic?

(i de-fragged the XP portion before attempting the install)
((on a 90GB hd, XP only takes 20GB so there SHOULD be room))

CE

---

### Post by Zimmer on 2009-06-15
> **CrimsonEclipse said:**
> I'm trying to install 9.04 on a disk with XP3 already.
It's a HP DV1000.

The 9.04 has a disk partition that has:
XP
The back up section (likely an image of XP)

Using the 9.04 partition, it tries to make extra space for 9.04 but I get a general error message. 

Should I use partition magic?

(i de-fragged the XP portion before attempting the install)
((on a 90GB hd, XP only takes 20GB so there SHOULD be room))

CE

Yes there SHOULD be room, but Windows may not want you to have it!!
When I was seting up a dual boot with Vista the partition software would not let me shrink the Vista partition below 70 gb.(HDD of 160 gb).

As yet have not found documentation to clarify why, but I gave in letting Vista have its way...

Your general error may be linked to the space that Windows XP wants as it may put System files in a particular memory spot on the partition( maybe nearly halfway along the drive...) , thus hogging space . 

40 gb for an Ubuntu (however you organise it ) will be plenty... 

Suggest when you try to partition  see this.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

---

### Post by CrimsonEclipse on 2009-06-15
Yeah I tried that with 9.04 and 8.04 with no dice. 

I'm thinking for forcing the issue with a 3rd party partition program. 

CE

---

### Post by Zimmer on 2009-06-16
Had a look at the GPARTED help re Windows partitions (available on the Jaunty LIVE CD) . Plenty of hints and MUSTS !

Disabling the pagefile before defrag, rebooting, running chkdisk, defragging AGAIN! before attempting to resize, then once resized to reboot and allow Windows chkdisk to run...
[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)
[http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-usage](http://gparted.sourceforge.net/docs/help-manual/C/gparted_manual.html#gparted-usage)
..from the above link..
> Tip

To improve the ability to shrink NTFS partitions, you might consider one or more of the following:

    *

      Defragment the file system.

      Booting into Safe Mode with the commercial operating system that uses NTFS can improve the ability to defragment the file system. To enter Safe Mode press F8 while your computer is booting the operating system.
    *

      Check the partition for errors with the following command:

      C:> chkdsk /f /r

      Remember to reboot back into the commercial operating system that uses NTFS to allow the chkdsk command to execute.
    *

      Temporarily disable the paging file. The paging file occupies a fixed location in the partition that the defragmentation process is unable to move.
    *

      Temporarily move large files to another partition or disk device. Large files are defined as greater than a few hundred Megabytes (MB).
    *

      Ensure a proper shut down of the commercial operating system that uses NTFS before you resize the NTFS partition
    *

      Leave at least 10 percent unused space in the NTFS partition. If you shrink the partition too much, then the commercial operating system might have difficulty functioning properly.
    *

      Reboot twice into the commercial operating system that uses NTFS after shrinking the NTFS partition. 
Hope this is of use to you...
Regards
Zimmer

---

