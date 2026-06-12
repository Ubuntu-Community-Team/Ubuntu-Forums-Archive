---
title: "cdrom issue"
date: 2008-06-16
forum: Hardware
---

### Post by nunki on 2008-06-16
I have a very strange cdrom issue. Currenly I have a Sony DVD-ROM DDU1642. This is a new DVDRom that replaces an older dvdrom that seemed to be going bad (whenever you ejected the cd, the cd would always be caught above the tray and get scratched. Seemed like it wasnt spinning down before it ejected). I got this one 2 days ago, and it does the same thing! This has to be a software issue.

Relevant lshw
```

*-cdrom
             description: DVD reader
             product: DVD-ROM DDU1642
             vendor: SONY
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrom1
             logical name: /dev/dvd
             logical name: /dev/dvd1
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: CS07
             capabilities: removable audio dvd
             configuration: ansiversion=5 status=open

```

Relevant fstab
```

/dev/scd0        /media/cdrom   udf,iso9660 user,noauto,exec 0       0

```

Relevant mtab
```

dev/scd0 /media/cdrom0 iso9660 ro,nosuid,nodev,user=**** 0 0

```

Another anomaly is that right clicking on the cd and choosing "eject" gives an error "Can't eject volume". Typing eject on the command line did not work until I created a symbolic link from /dev/scd0 to /dev/cdrom

Any ideas about what is going on? CD's/DVD's work fine, just that I scratch the heck out of them trying to get them out of the drive.

---

