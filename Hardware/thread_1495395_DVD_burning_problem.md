---
title: "DVD burning problem"
date: 2010-05-28
forum: Hardware
---

### Post by Loki*PI on 2010-05-28
This is a long standing problem I've run at several times with no good results; trying again.

I can neither read nor write CD or DVDs.

Using Karmic 9.10   

ASUS DRW-2014S1T DVD/CD burner SATA  

Using Brasero,GnomeBaker, and K3b all with pretty much the same results.  Brasero and K3b do not see the drive at all, GnomeBaker sees it but cannot see a disk in it.

Disk Utility sees the burner and correctly identifies it.


ls -l /media
total 4
lrwxrwxrwx 1 root root    6 2008-05-23 03:50 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-05-23 03:50 cdrom0


Here is error output from GnomeBaker when run as sudo:

TOC Type: 3 = CD-ROM XA mode 2
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.
scsidev: '/dev/sr0'
devname: '/dev/sr0'
scsibus: -2 target: -2 lun: -2
Linux sg driver version: 3.5.27
Wodim version: 1.1.9
SCSI buffer size: 64512
wodim: Cannot do inquiry for CD/DVD-Recorder.
Errno: 5 (Input/output error), test unit ready scsi sendcmd: fatal error
CDB:  00 00 00 00 00 00
cmd finished after 0.000s timeout 40s

I'm not sure what all this means but the 4th line from bottom seems the issue:  cannot do inquiry.

Here is lswh - short:

                                 system      System Product Name
/0                                bus         P5GC-MX/1333
/0/0                              memory      64KiB BIOS
/0/4                              processor   Intel(R) Pentium(R) Dual  CPU  E21
/0/4/5                            memory      64KiB L1 cache
/0/4/6                            memory      1MiB L2 cache
/0/4/1.1                          processor   Logical CPU
/0/4/1.2                          processor   Logical CPU
/0/2e                             memory      1GiB System Memory
/0/2e/0                           memory      1GiB DIMM DDR2 Synchronous 266 MHz
/0/2e/1                           memory      DIMM [empty]
/0/1                              processor   
/0/1/1.1                          processor   Logical CPU
/0/1/1.2                          processor   Logical CPU
/0/100                            bridge      82945G/GZ/P/PL Memory Controller H
/0/100/1                          bridge      82945G/GZ/P/PL PCI Express Root Po
/0/100/1/0                        display     RV370 [Sapphire X550 Silent]
/0/100/1/0.1                      display     RV370 secondary [Sapphire X550 Sil
/0/100/1b                         multimedia  82801G (ICH7 Family) High Definiti
/0/100/1c                         bridge      82801G (ICH7 Family) PCI Express P
/0/100/1c.1                       bridge      82801G (ICH7 Family) PCI Express P
/0/100/1c.1/0        eth1         network     L2 100 Mbit Ethernet Adapter
/0/100/1d                         bus         82801G (ICH7 Family) USB UHCI Cont
/0/100/1d.1                       bus         82801G (ICH7 Family) USB UHCI Cont
/0/100/1d.2                       bus         82801G (ICH7 Family) USB UHCI Cont
/0/100/1d.3                       bus         82801G (ICH7 Family) USB UHCI Cont
/0/100/1d.7                       bus         82801G (ICH7 Family) USB2 EHCI Con
/0/100/1e                         bridge      82801 PCI Bridge
/0/100/1f                         bridge      82801GB/GR (ICH7 Family) LPC Inter
/0/100/1f.1          scsi0        storage     82801G (ICH7 Family) IDE Controlle
/0/100/1f.1/0.1.0    /dev/sda     disk        80GB WDC WD800JB-00ET
/0/100/1f.1/0.1.0/1  /dev/sda1    volume      74GiB EXT3 volume
/0/100/1f.2          scsi2        storage     82801GB/GR/GH (ICH7 Family) SATA I
/0/100/1f.2/0.0.0    /dev/sdb     disk        250GB WDC WD2500AAJS-2
/0/100/1f.2/0.0.0/1  /dev/sdb1    volume      93GiB EXT3 volume
/0/100/1f.2/0.0.0/2  /dev/sdb2    volume      956MiB Linux swap volume
/0/100/1f.2/0.0.0/3  /dev/sdb3    volume      138GiB EXT3 volume
/0/100/1f.2/0.1.0    /dev/cdrom2  disk        DVD-RAM writer
/0/100/1f.3                       bus         82801G (ICH7 Family) SMBus Control

I have tried swapping burners.  I have an XP box both burners work in it, but neither work with Ubuntu. 

When I first converted to Ubuntu I didn't have this problem, it is with the last three releases that I've had DVD/CD issues.  I was hoping Karmic would resolve this but no luck.  Any suggestions would be appreciated.  Thanks all.

---

### Post by anglican on 2010-05-28
> **Loki*PI said:**
> This is a long standing problem I've run at several times with no good results; trying again.

I can neither read nor write CD or DVDs.

Using Karmic 9.10   

ASUS DRW-2014S1T DVD/CD burner SATA  

Using Brasero,GnomeBaker, and K3b all with pretty much the same results.  Brasero and K3b do not see the drive at all, GnomeBaker sees it but cannot see a disk in it.

Disk Utility sees the burner and correctly identifies it.


ls -l /media
total 4
lrwxrwxrwx 1 root root    6 2008-05-23 03:50 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-05-23 03:50 cdrom0


Here is error output from GnomeBaker when run as sudo:

TOC Type: 3 = CD-ROM XA mode 2
wodim: No write mode specified.
wodim: Asuming -tao mode.
wodim: Future versions of wodim may have different drive dependent defaults.

(snip)

I have tried swapping burners.  I have an XP box both burners work in it, but neither work with Ubuntu. 

When I first converted to Ubuntu I didn't have this problem, it is with the last three releases that I've had DVD/CD issues.  I was hoping Karmic would resolve this but no luck.  Any suggestions would be appreciated.  Thanks all.
In my experience,  on different hardware, wodim may be the  problem. I replaced it with the original [cdrtools]("http://cdrecord.berlios.de/private/cdrecord.html") that wodim is a fork  from and problems all went away. YMMV.

H

---

### Post by Loki*PI on 2010-05-28
Hi:  Thanks for responding.  Wow I've been reading the cdrtools vs: wodim information.  That is over my head.  The modifications required to install the original tools cdrtools appears extensive, and then when I do an update there could be problems.  

I think I need a more community supported solution.  This is a pretty basic function for an OS these days, to be able to read and write a CD/DVD.  Ubuntu must have some support solution for this.

---

### Post by ssulaco on 2010-05-29
This may or may not help you....
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by jerrrys on 2010-05-29
is this  a fresh install of 910 or upgrade?

---

### Post by Loki*PI on 2010-05-31
Thanks for the suggestions.  I upgraded to Locid hoping that might solve the problem but it appears to have the same issues.  I havent' had time to do much testing but doesnt' look good.  Still open to suggestions.

---

### Post by lidex on 2010-05-31
What do these entries in /dev link to?
```
cdrom
cdrom0
dvd
cdrw
dvdrw
scd0
```

---

### Post by salemboot on 2010-06-05
[http://www.nero.com/enu/linux4.html](http://www.nero.com/enu/linux4.html)


Works fine with my external burner.  I have an InfoMagic.:guitar:

---

### Post by Loki*PI on 2010-06-16
Hi Lidex:  Thanks for responding.  /dev is a folder so I'm not sure what you are asking me or how to get the info.  I'm pretty much a nubie here.

---

### Post by anglican on 2010-06-17
> **Loki*PI said:**
> Hi Lidex:  Thanks for responding.  /dev is a folder so I'm not sure what you are asking me or how to get the info.  I'm pretty much a nubie here.
Try opening a terminal and typing:
```
ls -l /dev/cd* /dev/dvd* /dev/scd*
```H

---

### Post by Loki*PI on 2010-06-17
Thanks anglican and all.  

output for sudo ls -l /dev/cd* /dev/dvd* /dev/scd* :
ls: cannot access /dev/cd*: No such file or directory
ls: cannot access /dev/dvd*: No such file or directory
ls: cannot access /dev/scd*: No such file or directory

I have tried several configurations in /etc/fstab the current one is:
/dev/scd0 /media/cdrom0 iso9660,udf user,noauto,exec,utf8 0 0  This was recommend on one of the threads.  Using this "Places" shows cdrom0.  When I try to open it I get error  "special device /dev/scd0 does not exist"

Seems consistent with the results of the ls.  What is suppose to creat the entries in /dev?  Is there a way to force a rebuild? 

I'm at the far end of a slow connection. The update to Lucid took 18 hours. I'm hoping no one says to rebuild the system.

---

### Post by Loki*PI on 2010-06-17
To continue the story.  Today I had an error during the boot I haven't seen before.  The purple splash came up with an error saying /media/cdrom0 could not mount and gave me an option to skip the mount or go to manual.  When I skipped the mount it also skipped the hard drives and the system froze.  When I went to manual the system also froze.  I finally got in but it took numerous tries.  I have removed the /media/cdrom0 line in /etc/fstab, and the machine boots normally now.  

I'm at a loss here. I need to get some kind of entry into /dev like /dev/scd0 but I don't know what or how.  Also I'm thinking to go by another CD/DVD any one have a suggestion of one that will work with Ubuntu Lucid?  ASUS is pretty main stream but it is not coming together.  One last thought is to reformat and install lucid new.  Open to suggestions.  Thanks All

---

### Post by anglican on 2010-06-18
> **Loki*PI said:**
> To continue the story.  Today I had an error during the boot I haven't seen before.  The purple splash came up with an error saying /media/cdrom0 could not mount and gave me an option to skip the mount or go to manual.  When I skipped the mount it also skipped the hard drives and the system froze.  When I went to manual the system also froze.  I finally got in but it took numerous tries.  I have removed the /media/cdrom0 line in /etc/fstab, and the machine boots normally now.  
Right, that line in the fstab will cause problems booting if there is no drive/disk found.

> I'm at a loss here. I need to get some kind of entry into /dev like /dev/scd0 but I don't know what or how.  Also I'm thinking to go by another CD/DVD any one have a suggestion of one that will work with Ubuntu Lucid?  ASUS is pretty main stream but it is not coming together.  One last thought is to reformat and install lucid new.  Open to suggestions.  Thanks AllRe-formatting and re-installing is unlikely to help. What does:
```
wodim -scanbus
```show?

H

---

### Post by Loki*PI on 2010-06-18
Hi Again:  Thanks for following up:  Results:

wodim -scanbus
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

wodim --devices
wodim: No such file or directory. 
Cannot open SCSI driver!
For possible targets try 'wodim --devices' or 'wodim -scanbus'.
For possible transport specifiers try 'wodim dev=help'.
For IDE/ATAPI devices configuration, see the file README.ATAPI.setup from
the wodim documentation.

That doesn't look so good.

---

### Post by anglican on 2010-06-18
> **Loki*PI said:**
> Hi Again:  Thanks for following up:  Results:

...
wodim: No such file or directory. 
Cannot open SCSI driver!
...

That doesn't look so good.
No, it doesn't. What does:
```
sudo lshw -C disk -short
```give?

H

---

### Post by Loki*PI on 2010-06-18
sudo lshw -C disk -short
 
H/W path             Device     Class       Description
=======================================================
/0/100/1f.1/0.1.0    /dev/sda   disk        80GB WDC WD800JB-00ET
/0/100/1f.2/0.0.0    /dev/sdb   disk        250GB WDC WD2500AAJS-2

The two hard drives.  They are also SATA.  So they are being treated as SCSI.  The CD/DVD should just show as /dev/sdc.  I wondering if it is something with this drive.  I have another one I can swap out.  I've tried it before and it didn't work but that was a ways back.  Can't hurt to try; I hope.  

Thanks again

---

### Post by anglican on 2010-06-18
> **Loki*PI said:**
> sudo lshw -C disk -short
 
H/W path             Device     Class       Description
=======================================================
/0/100/1f.1/0.1.0    /dev/sda   disk        80GB WDC WD800JB-00ET
/0/100/1f.2/0.0.0    /dev/sdb   disk        250GB WDC WD2500AAJS-2

The two hard drives.  They are also SATA.  So they are being treated as SCSI.  The CD/DVD should just show as /dev/sdc.  I wondering if it is something with this drive.  I have another one I can swap out.  I've tried it before and it didn't work but that was a ways back.  Can't hurt to try; I hope.  

Thanks again
Right, the hardware just isn't showing up at all. Check all the connections are firmly in and try an alternate cable (if you have one) also a different SATA port might help. A different drive would certainly also be worth trying.

H

---

### Post by Loki*PI on 2010-06-18
The very odd thing is, once in a while the drive does show up.  Very rarely I've been able to read a disk. This is most common if I leave a disk in then boot.  I have put in the other drive and will try and get it working.

The ASUS drive, which was in this box, showed up with no problem in the XP box, and is working normally.

I'll update this later.

Thanks again for all the help.

---

### Post by Loki*PI on 2010-06-19
I've done some testing with the new drive.  It is a Lite-On Model HAS120 SATA.  Been working in the XP box for couple of years, no problem.

Additional information:

There is now a /dev entry: (progress!!)

sudo lshw -C disk -short
 
H/W path             Device       Class       Description
=========================================================
/0/100/1f.1/0.1.0    /dev/sda     disk        80GB WDC WD800JB-00ET
/0/100/1f.2/0.0.0    /dev/sdb     disk        250GB WDC WD2500AAJS-2
/0/100/1f.2/0.1.0    /dev/cdrom2  disk        iHAS120   6

ls -l /media
total 4
lrwxrwxrwx 1 root root    6 2008-05-23 03:50 cdrom -> cdrom0
drwxr-xr-x 2 root root 4096 2008-05-23 03:50 cdrom0


ric@zero:~$ ls -l /dev/cd* /dev/dvd* /dev/scd*
lrwxrwxrwx 1 root root 3 2010-06-19 11:40 /dev/cdrom2 -> sr0
lrwxrwxrwx 1 root root 3 2010-06-19 11:40 /dev/cdrw2 -> sr0
lrwxrwxrwx 1 root root 3 2010-06-19 11:40 /dev/dvd2 -> sr0
lrwxrwxrwx 1 root root 3 2010-06-19 11:40 /dev/dvdrw2 -> sr0
lrwxrwxrwx 1 root root 3 2010-06-19 11:40 /dev/scd0 -> sr0

Just doing hit and miss I have tried the following in /etc/fstab:  (none of which work)


/dev/cdrom2       /media/cdrom0   udf,iso9660 user,noauto     0       0

/dev/cdrom2 /media/cdrom0 udf, iso9660 user,noauto,exec,utf8 0 0

/dev/cdrom2 /media/cdrom0 iso9660, udf user,noauto,exec,utf8 0 0  (hung on boot)

Suggestions anyone?  Thanks All.

---

### Post by Loki*PI on 2010-06-19
I seem to have this resolved.  WOW!!!

I restored the default line, from long ago, in /etc/fstab:

 /dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0

The Lite-On CD/DVD seems to be working.  It doesn't show up in Places until a disk is inserted; I thought would.  I have tried Brasero Disk Burner and GnomeBaker and both seem to work.  I have burned a couple CD and a DVD.  Also read some old CDs and DVDs.  It all seems to be working.

Thanks everyone for the help, Especially anglican.

---

