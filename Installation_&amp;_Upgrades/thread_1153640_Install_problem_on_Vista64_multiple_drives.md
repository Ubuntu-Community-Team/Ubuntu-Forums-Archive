---
title: "Install problem on Vista64 multiple drives"
date: 2009-05-09
forum: Installation &amp; Upgrades
---

### Post by Pateris on 2009-05-09
[FONT=Verdana]I am trying to install Ubuntu 9.04 on my Vista x64 box (dual boot) and I have a problem.

I have multiple drives - but there are three that are important:

/dev/sda and /dev/sdb are two 500 GB drives, which I had setup using Intel ICH9R fakeRAID-0 under Windows.  The plan was to have a couple of 200 GB partitions for Windows and another pair of partitions for Linux.

/dev/sdc is a 70 GB drive, which is partitioned into a 50 GB NTFS partition (sdc1), leaving me 20 GB for /boot and /.

I thought that the easiest thing would be to install Ubuntu onto the 20 GB partition of /dev/sdc, but when I did that, the installed put GRUB on /dev/sda.  The problem being that this mangled the RAID config, and the BIOS is set to boot from /dev/sd3 (HD2) - so it tries to boot Vista (but Vista bluescreens on boot).

Can I fix it?  Or do I start from scratch again (I have images of all the Vista partitions backed up)?  And if I start from scratch, how do I make sure Ubuntu's installed puts GRUB on /dev/sdc?
[/FONT]

---

### Post by BooNality on 2009-05-09
Oh wow, I "think" you can fix it but I don't know how.  I had an issue with GRUB earlier today where it suddenly gave me 2 of ubuntu and recovery mode to select from when I only have one distro installed, and to fix it I used this...

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

The link is geared toward recovering GRUB after a Windows isntall over an already good GRUB config but it has alot of information in there and I was able to use this guide to remove a copy of my ubuntu and recovery mode from the GRUB menu so now it is correct again and looking the way it should.

---

### Post by cariboo on 2009-05-09
Have a look at this [thread=224351]howto[/thread] and as well maybe have a look at the [FakeRaid Howto]("http://help.ubuntu.com/community/FakeRaidHowto")

---

### Post by Pateris on 2009-05-09
I think what I am going to try to do is a hardware trick.

I'm going to change which drives are plugged into which SATA ports on the MB.

That way the boot drive will be /dev/sda and hd0 to both operating systems and I won't need to worry about trying to figure out the MBRs on the fakeRAID...

---

### Post by Pateris on 2009-05-09
OK, I've gotten Ubuntu up an running after switching which harddrives were on which ports. 

/dev/sda is hd0 and is the 74 GB boot drive
/dev/sdb and /dev/sdc are *supposed *to be in a RAID 0.

When I start the machine, my Intel ICH9R controller tells me that the two disks in the RAID are OFFLINE MEMBERS.   I think this is because of this (from bootinforscript):

```
============================= Boot Info Summary: ==============================

 => Grub0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #2 for /grub/stage2 and /grub/menu.lst.
 => Grub0.97 is installed in the MBR of /dev/sdb and looks on boot drive #3 in 
    partition #2 for /grub/stage2 and /grub/menu.lst.
 => Windows is installed in the MBR of /dev/sdc

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda2: _________________________________________________________________________

    File system:       ext2
    Boot sector type:  -
    Boot sector info:  
    Operating System:  
    Boot files/dirs:   /grub/menu.lst

sda3: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

sda4: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.04
    Boot files/dirs:   /boot/grub/menu.lst /etc/fstab

sdb1: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdb2: _________________________________________________________________________

    File system:       
    Boot sector type:  -
    Boot sector info:  
    Mounting failed:
mount: unknown filesystem type ''

sdc1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   
```

My big question is:  How do I repair the MBR on /dev/sdb back to a Windows Vista MBR? (which is why I think the RAID is screwed up...)

---

### Post by Pateris on 2009-05-10
OK - the hardware thing did the trick.


[LIST]
[*]Ubuntu installed and booting from /dev/sda (hd0,1).
[*]On restart, Intel ICH9R RAID says two disks are OFFLINE MEMBERS
[*]Vista boots from hd0,0 without the RAID working at all
[*]On a second restart. Intel ICH9R RAID says two disks are ONLINE
[*]Vista boots from hd0,0 **with** the RAID functioning.
[*]Only problem is that because I had the Vista /USERS/ directory on a RAID partition, the boot into Vista without the RAID locked up my profile - still trying to work that out.
[/LIST]
Now we'll see if I can get Ubuntu to see the RAID so I can move /home there...

---

