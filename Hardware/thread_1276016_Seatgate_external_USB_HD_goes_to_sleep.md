---
title: "Seatgate external USB HD goes to sleep"
date: 2009-09-26
forum: Hardware
---

### Post by kudude on 2009-09-26
Hello,

I don't know if this is a problem that can be solved, but I have an issue with my external hard drive.  I store a lot of video and music on it, so it isn't used regularly for internet browsing/email, etc.

Whenever I try to access it, there is about a 5 second wait for the drive to be pinged and then spin up.  This is annoying.  Annoying enough that I try to "ls /media/audio" whenever I think I might want access to my music, so I don't have to wait the 5-7 seconds.  Does anyone know of a mounting option that keeps it awake, or is my best bet to set up some sort of weird cron job to run every 8 minutes to try to access the drive?

Thank you

---

### Post by txwooley on 2009-09-26
There's a lot of info out there about Seagate not playing nice with Linux because of this.  What worked for me is to make sure the HDD is installed and awake.  Then in a terminal type (this only works if you have sdparm installed.  if not then go get it from the package manager or using apt-get):

```
$ sudo fdisk -l

```

Note the name of your external HDD.  It should be something similar to "/dev/sdb"

```

$ sudo sdparm --clear STANDBY -6 /dev/sdb

```

Where /dev/sdb is the appropriate name of your drive.

That should stop it from sleeping.  Hope this helps.

---

### Post by kudude on 2009-09-27
> **txwooley said:**
> There's a lot of info out there about Seagate not playing nice with Linux because of this.  What worked for me is to make sure the HDD is installed and awake.  Then in a terminal type (this only works if you have sdparm installed.  if not then go get it from the package manager or using apt-get):

```
$ sudo fdisk -l

```Note the name of your external HDD.  It should be something similar to "/dev/sdb"

```

$ sudo sdparm --clear STANDBY -6 /dev/sdb

```Where /dev/sdb is the appropriate name of your drive.

That should stop it from sleeping.  Hope this helps.


Thanks.  That worked.  I really appreciate it.

---

