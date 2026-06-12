---
title: "CD ROM Cache"
date: 2015-08-02
forum: Hardware
---

### Post by drmynatt on 2015-08-02
Hi group-  I am using 12.04 on an older machine with a new CD ROM drive. I loaded a CD ROM data disk and it showed in the CDROM subdir off the root. However, when I loaded the next disk, a DIR of the disk showed the original data and not the new data. Weird. In other words, it appears my CD ROM cache (if there is such a thing) is not being overwritten or deleted when I load a new CD ROM disk; I get the same info no matter how many disks I try.

Here's some terminal outputs:

```
sudo lsblk -f
NAME   FSTYPE LABEL MOUNTPOINT
sda                 
&#9500;&#9472;sda1 ext4         /
&#9500;&#9472;sda2              
&#9492;&#9472;sda5 swap         [SWAP]
sr0                 

dave@ubuntu-desk:~$ cd-info --no-cddb-cache
cd-info version 0.83 i686-pc-linux-gnu
Copyright (c) 2003, 2004, 2005, 2007, 2008, 2011 R. Bernstein
This is free software; see the source for copying conditions.
There is NO warranty; not even for MERCHANTABILITY or FITNESS FOR A
PARTICULAR PURPOSE.
CD location   : /dev/cdrom
CD driver name: GNU/Linux
   access mode: IOCTL

Vendor                      : HL-DT-ST
Model                       : CD-RW GCE-8483B 
Revision                    : B105
Hardware                                  : CD-ROM or DVD
Can eject                                 : Yes
Can close tray                            : Yes
Can disable manual eject                  : Yes
Can select juke-box disc                  : No

Can set drive speed                       : No
Can read multiple sessions (e.g. PhotoCD) : Yes
Can hard reset device                     : Yes

Reading....
  Can read Mode 2 Form 1                  : Yes
  Can read Mode 2 Form 2                  : Yes
  Can read (S)VCD (i.e. Mode 2 Form 1/2)  : Yes
  Can read C2 Errors                      : Yes
  Can read IRSC                           : Yes
  Can read Media Channel Number (or UPC)  : Yes
  Can play audio                          : Yes
  Can read CD-DA                          : Yes
  Can read CD-R                           : Yes
  Can read CD-RW                          : Yes
  Can read DVD-ROM                        : No

Writing....
  Can write CD-RW                         : Yes
  Can write DVD-R                         : No
  Can write DVD-RAM                       : No
  Can write DVD-RW                        : No
  Can write DVD+RW  
```

Help very much appreciated as I have very important wedding pictures on a disk I cannot read.  Thanks in advance,

Dave

---

### Post by weatherman2 on 2015-08-02
I have had this problem occasionally in different versions of Ubuntu (not every version for some reason).  I don't know the best solution, but one way to get around it is to eject the disk before inserting a new one - have you tried that?  By "Eject" I don't mean use the button - I mean, right-click on the CD-ROM and choose "Eject" or "Safely Remove" or whatever...

---

### Post by drmynatt on 2015-08-02
Yes; eject and I even removed drive in BIOS and it still shows the same data. Is there a way to clean the cache or have I mounted it wrong?

Have I posted the right info/enough info about the system or CD ROM?

Here's what Terminal Command shows:

dave@ubuntu-desk:/cdrom$ eject
eject: unable to eject, last error: Inappropriate ioctl for device
dave@ubuntu-desk:/cdrom$

I saw this on another post, and this sequence ejects/opens the CD ROM tray:

1. 'sudo eject /dev/sr0'
2. 'file /dev/sr0'
3. 'sudo eject -i off'

Then...

dave@ubuntu-desk:/$ eject cdrom

Works OK.

However, now can't get anything to read from CD ROM.

---

### Post by weatherman2 on 2015-08-02
Instead of ejecting, try unmounting the disk - then physically ejecting it:

```
sudo umount /dev/sr0
```

---

### Post by drmynatt on 2015-08-02
Here's the results of these commands:

dave@ubuntu-desk:/$ sudo umount /dev/sr0
[sudo] password for dave: 
umount: /dev/sr0: not mounted
dave@ubuntu-desk:/$ sudo mount /dev/sr0
mount: can't find /dev/sr0 in /etc/fstab or /etc/mtab
dave@ubuntu-desk:/$ 

Does it look like I mis-mounted or improperly installed something?

---

### Post by weatherman2 on 2015-08-02
OK - so, you reboot, insert a CD...and you can read it right?

Then you eject or remove it and can't read another CD - ever?  Or until you reboot?

Try the umount command when the first readable CD is still in the tray and readable...

---

### Post by drmynatt on 2015-08-02
Reboot leaves same problem; cannot get anything to show when doing LS or DIR from command line, or when accessing CDROM subdir icon from File System. No files show.

---

### Post by weatherman2 on 2015-08-02
OK just to be clear: you originally installed Ubuntu, then inserted say CD #1, and since then, Ubuntu thinks CD #1 is still in the drive, no matter how many times you reboot?

In other words, if you remove all discs reboot, and insert CD #2, Ubuntu still thinks CD #1 is installed?

I was assuming that once you reboot with no CD then inset a new CD, you'd be able to read the new CD- not true?

---

### Post by drmynatt on 2015-08-02
Weird, huh. But that's about it. The install is about a year old and I used a CD to install Ubuntu. Since then I really haven't used the drive. Then I took pictures at my wedding. In the between time, I placed a CD in the drive that had just files on it (history stuff from my study). I saw all them. Then, today, I placed the CD in the drive that had my wedding pictures on it and, well, only the old files (history files) showed.  Cannot see the wedding pictures but do see the files from the 'history' CD.  Then did the above sequences and still no luck; all I see is the 'history' files. I un-installed the drive in the BIOS and rebooted and then went back and restarted Ubuntu and went into the BIOS and put the drive back in, and still just the old files.  Using the File Manager, then File System, I have MNT, CDROM and Media subdirs off Root. No matter what I see only 'history' files; no matter what CD I put in the drive, when, or how.

Does this help?

dave@ubuntu-desk:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=d96facca-81ad-4804-8ab6-6f93a7a6416b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=95e05011-f352-4d33-9747-2eaa8671a424 none            swap    sw              0       0

I've tried  about everything. I lastly tried wodim. The CD ROM shows... Here's that output:

dave@ubuntu-desk:/$ wodim --devices
wodim: Overview of accessible drives (1 found) :
-------------------------------------------------------------------------
 0  dev='/dev/sg1'	rwrw-- : 'HL-DT-ST' 'CD-RW GCE-8483B'
-------------------------------------------------------------------------

dave@ubuntu-desk:/$ ls -al /dev/cdrom*
lrwxrwxrwx 1 root root 3 Aug  2 20:25 /dev/cdrom -> sr0
dave@ubuntu-desk:/$ sudo mount -t iso9660 /dev/sr0 /media/cdrom
mount: block device /dev/sr0 is write-protected, mounting read-only
mount: no medium found on /dev/sr0

I'm an idiot. Situation normal as my wife says. Disregard all above and remember that if idiots need love.

---

