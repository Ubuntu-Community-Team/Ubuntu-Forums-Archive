---
title: "fstrim causing read-only file system"
date: 2017-09-11
forum: Hardware
---

### Post by melmacjim on 2017-09-11
Hello all. This is my first post and I'll try to keep it short and to the point.

I'll start by stating that the smartctl data has yet to produce a negative report (I always see a `PASS` report after 5 minutes of running `sudo smartctl -t long /dev/sda`).

I have over 600 systems all running Ubuntu 16.04 with kernel release 4.4.0-31-generic and they also all have the default fstrim script in their cron.weekly directory (`/etc/cron.weekly/fstrim`).

For the past few weeks I've been seeing about 15 systems go read-only at 06:47:01 (some a little before and some a little after) Sunday morning which is the same time the `/etc/cron.weekly` jobs are executed.

I also haven't yet been able to reproduce the issue by running `sudo fstrim --all` manually.

I reached out to Apacer and they said *"... we do not recommend users to use TRIM function under Linux system because it is a 3rd party command ..."* after I pointed them to the `/etc/cron.weekly/fstrim` script and the `/sbin/fstrim` executable.

Has anyone ever had issues with fstrim causing their ext4 file system to go read-only?
Does anyone have any experience using Apacer SSD's with Ubuntu 16.04 with ext4 as their root file system? And if so, have you had any file system issues of any kind?
Has anyone disabled the `/etc/cron.weekly/fstrim` cronjob? If so, how long has it been disabled and have there been any negative side effects? 
Any advise on TRIM and/or Apacer SSD's is also welcome.

I haven't see any posts regarding `fstrim` putting a file system into a read-only state (not using any RAID; each system has one SSD) but if anyone can point me to something related, that would be appreciated.
Any feedback is welcome.

Below is some relevant information regarding my systems:
```

$ uname -a
Linux hostname 4.4.0-31-generic #50-Ubuntu SMP Wed Jul 13 00:07:12 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

$ cat /etc/fstab
...
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=9f46ed5f-a145-4f6c-ab68-78c13c355e7a /               ext4    barrier=1,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=436a9062-c262-4303-a933-cf1fc5040468 none            swap    sw              0       0

$ sudo fdisk -l /dev/sda
...
Device     Boot     Start       End   Sectors   Size Id Type
/dev/sda1  *         2048 241938431 241936384 115.4G 83 Linux
/dev/sda2       241940478 250068991   8128514   3.9G  5 Extended
/dev/sda5       241940480 250068991   8128512   3.9G 82 Linux swap / Solaris

$ cat /etc/cron.weekly/fstrim 
#!/bin/sh
# trim all mounted file systems which support it
/sbin/fstrim --all || true

$ sha256sum /sbin/fstrim 
16776b8682093752aed201e42f86a0d6bf78bfd8e402df350543354ed9e5bf75  /sbin/fstrim

$ sudo hdparm -I /dev/sda | grep TRIM
       *    Data Set Management TRIM supported (limit 8 blocks)

```

Thanks

---

