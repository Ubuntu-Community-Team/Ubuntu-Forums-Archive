---
title: "cdrecord burning problem!"
date: 2006-08-28
forum: Hardware &amp; Laptops
---

### Post by patrihito on 2006-08-28
Hi all,

is there anybody out there that can help me solve my problem?

I'm not able to burn with my laptop using gnomebaker or k3b...

Here's the error I get from gnomebaker:
```
cdrecord: Warning: Running on Linux-2.6.15-23-686
cdrecord: There are unsettled issues with Linux-2.5 and newer.
cdrecord: If you have unexpected problems, please try Linux-2.4 or Solaris.
scsidev: '1,0,0'
scsibus: 1 target: 0 lun: 0
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Error trying to open /dev/sg0 exclusively (Permission denied)... retrying in 1 second.
Cdrecord-Clone 2.01.01a01 (i686-pc-linux-gnu) Copyright (C) 1995-2004 Joerg Schilling
NOTE: this version of cdrecord is an inofficial (modified) release of cdrecord
      and thus may have bugs that are not present in the original version.
      Please send bug reports and support requests to <cdrtools@packages.debian.org>.
      The original author should not be bothered with problems of this version.

TOC Type: 1 = CD-ROM
cdrecord: Permission denied. Cannot open '/dev/sg0'. Cannot open SCSI driver.
cdrecord: For possible targets try 'cdrecord -scanbus'. Make sure you are root.
cdrecord: For possible transport specifiers try 'cdrecord dev=help'.
cdrecord: 
cdrecord: For more information, install the cdrtools-doc
cdrecord: package and read /usr/share/doc/cdrecord/README.ATAPI.setup .
```

Any ideas?

Thanks a lot.
Patrihito

---

### Post by croak77 on 2006-08-28
Are you using a normal user or sudo? There is a bug which makes gnomebaker work only as root.

---

### Post by patrihito on 2006-08-29
> **croak77 said:**
> Are you using a normal user or sudo? There is a bug which makes gnomebaker work only as root.

Sorry, how do I use gnomebaker as root?

Thanks a lot.

Patrihito

---

### Post by croak77 on 2006-08-29
Open a terminal and type;

```
gksudo gnomebaker
```

---

### Post by ThrobbingBrain66 on 2006-08-29
this thread fixed my problems with k3b....

[http://www.ubuntuforums.org/showthread.php?t=217472&highlight=burning+issues](http://www.ubuntuforums.org/showthread.php?t=217472&highlight=burning+issues)

---

### Post by patrihito on 2006-08-29
> **croak77 said:**
> Open a terminal and type;

```
gksudo gnomebaker
```

This one is okay for me!

Thanx a lot!:D 
Patrihito

---

