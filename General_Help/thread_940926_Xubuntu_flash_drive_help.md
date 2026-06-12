---
title: "Xubuntu flash drive help"
date: 2008-10-07
forum: General Help
---

### Post by silkesvarten on 2008-10-07
Hello.

I just installed Xubuntu on my laptop, and it mostly works great.
Unfortunately though, I couldn't get a good install from my CDROM drive, so i made a bootable flash drive, and installed it from that.
 
The problem now is that it fails to mount flash drives. I get the error message: Unable to mount "PINNE":

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I tried dmesg | tail, and heres what I found:

daniel@daniel-laptop:~$ dmesg | tail
[  914.865279] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  914.868260] sd 7:0:0:0: [sdb] 7897087 512-byte hardware sectors (4043 MB)
[  914.869012] sd 7:0:0:0: [sdb] Write Protect is off
[  914.869019] sd 7:0:0:0: [sdb] Mode Sense: 00 00 00 00
[  914.869023] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[  914.869030]  sdb: sdb1
[  391.549732] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  391.549777] sd 7:0:0:0: Attached scsi generic sg2 type 0
[  392.115051] UDF-fs: No VRS found
[  392.159480] ISOFS: Unable to identify CD-ROM format.


If I'm interpreting this correctly, the system thinks that the USB-drive is a CDROM?

Any thing I can do to fix this?

Thanks for reading.

Daniel

---

### Post by DagMan on 2008-10-07
Yeah it does that when you install from usb.  You have to fix one file.

I installed from USB and I just commented out my line in the /etc/fstab file so I'll use it as an example.

I have this in there that needed to be commented out

```
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

```

If you have a cdrom drive, then instead of commenting it out, change where it says /dev/sdb1 to the optical drive device.
it likely will look like this
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

see if that works, to make the line referring to /media/cdrom0 either look like the second example here, or just get rid of it entriely if you don't have a cd or dvd drive.

---

### Post by silkesvarten on 2008-10-08
Hey.

It was as you said, and now it works. 

Thanks for the help

Daniel

---

