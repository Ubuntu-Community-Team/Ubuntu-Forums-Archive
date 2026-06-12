---
title: "Corrupt files"
date: 2015-11-10
forum: Hardware
---

### Post by M_D on 2015-11-10
About a week a go I started having a problem with files being downloaded getting corrupted.  So far I've not come across any existing files as getting corrupted only new files.  I presume this is a failing drive problem.  This is a software raid 6 array with ext4 filesystem.  I've ran smart test on all the drives and not showing any bad blocks on any of them, I've ran a filesystem check it did it's thing and shows clean.  Is there a way to find out which sectors are bad in a file and which drive in the array the sectors are landing?  Or if I am heading in the completely wrong direction?

Running Ubuntu 14.04.3 LTS (GNU/Linux 3.13.0-67-generic x86_64)

---

### Post by weatherman2 on 2015-11-10
Check the S.M.A.R.T. Attributes on each drive.  Use a program called GSmartControl - lets you do more than the built-in disk utility in Ubuntu.  

Are there any lines highlighted in the GSmartControl Attributes in red or pink for each drive?  Pending sectors?  Reallocated sectors?  If not, I'd say the hard drives are not failing.

You can force a check with e2fsck even if it shows clean, by the way.

Still, one might ask what exactly you mean by "corrupted?"  How do you know?  Trying to open a file?  Errors trying to copy it?  Try downloading one specific file on this computer and also on some other device and make sure it opens correctly on the known good device but fails on your suspect Ubuntu system.

---

### Post by M_D on 2015-11-10
> **weatherman2 said:**
> Check the S.M.A.R.T. Attributes on each drive.  Use a program called GSmartControl - lets you do more than the built-in disk utility in Ubuntu.  

Are there any lines highlighted in the GSmartControl Attributes in red or pink for each drive?  Pending sectors?  Reallocated sectors?  If not, I'd say the hard drives are not failing.

I don't have a UI but I have ran smartctl to see if there are SMART errors and there are not any.


> **weatherman2 said:**
> You can force a check with e2fsck even if it shows clean, by the way.

I know, I did.

> **weatherman2 said:**
> Still, one might ask what exactly you mean by "corrupted?"  How do you know?  Trying to open a file?  Errors trying to copy it?  Try downloading one specific file on this computer and also on some other device and make sure it opens correctly on the known good device but fails on your suspect Ubuntu system.

I first noticed the problem on files that wouldn't open properly.  I did some testing with rar files that had 1000 segments and I would get bad checksums when extracting the file, I can redownload the segments that report bad and it will then extract fine.

---

### Post by weatherman2 on 2015-11-10
OK - I'm not asking about "smart errors" - I'm asking about the attributes saved by each drive's firmware - these are various indicators of the drive health and status.  Even if there are no S.M.A.R.T. errors recorded, you could still have bad sectors showing in the attributes.

With smartctl, do this for each drive from a terminal:

```
sudo smartctl -A /dev/sda | grep Sector
```

(Repeat for /dev/sdb etc.)

The last column is the raw value of the attribute.  If they are all zeros, then there are no bad sectors according to S.M.A.R.T.  In that case, I'd rule out drive failure.  And it sounds like you can rule out file system problems if you ran a full e2fsck .

Beyond that, I don't know how you are downloading these files.  Attach another device - thumb drive, whatever - and try downloading to this device instead of to your RAID.  If you can download to that device without corruption but still get corruption when downloaded to the RAID, then you indeed are having some issue with the RAID.  But if you have the same "corruption" problems even when downloading to another device, you can rule out the RAID entirely.

---

### Post by M_D on 2015-11-10
```
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdb | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdc | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdd | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sde | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdf | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdg | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdh | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdi | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdj | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdk | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   010    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdl | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdm | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdn | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
md@tv-*****:~/media/16TBR5V1/test$ sudo smartctl -A /dev/sdo | grep Sector
  5 Reallocated_Sector_Ct   0x0033   100   100   005    Pre-fail  Always       -       0
197 Current_Pending_Sector  0x0022   100   100   000    Old_age   Always       -       0
```

Usually copy files via cifs or ftp.  I went a head and pulled /dev/sdf out of the array and am testing.  So far no corrupted files.

---

