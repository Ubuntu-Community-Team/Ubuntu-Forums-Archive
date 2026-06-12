---
title: "Can't print: Cups says &quot;Filter failed&quot;"
date: 2014-07-17
forum: Hardware
---

### Post by TheBigH on 2014-07-17
Hi everyone,
I recently installed Ubuntu 14.04 on a new computer and my old Lexmark 1290 printer now won't work. I had previously installed it following on another machine with Ubuntu 12.04 following the instructions here:
 [http://ubuntuforums.org/showthread.php?t=49714&page=57](http://ubuntuforums.org/showthread.php?t=49714&page=57)
and had no problems.

Now when I do the same on the new computer I cannot get anything to print at all. According to Cups 1.7.2, the printer's status is ```
Idle - Rendering completed
``` and the failed print job's status is ```
Stopped "Filter failed"
```

Does anyone know what is happening and how to fix it?

---

### Post by frederic-durodie on 2014-08-07
Hi,

 did you have any solution to this issue : I have the same problem
(I'm using the lexmark.z600-0.4.deb package on 14.04 64-bit which works correctly on all my other  12.04 32/64 bit ubuntus)

---

### Post by frederic-durodie on 2014-08-08
OK. I fixed the problem by looking at the /var/log/cups/error_log and finding the line :

> D [08/Aug/2014:13:43:14 +0200] [Job 256] Dell-A920: error while loading shared libraries: libcupsimage.so.2: cannot open shared object file: No such file or directory

I installed the missing library according instrunctions found in  [http://misterpinchy.wordpress.com/2013/01/28/dell-1350cnw-lazer-printer-on-ubuntu-x64/](http://misterpinchy.wordpress.com/2013/01/28/dell-1350cnw-lazer-printer-on-ubuntu-x64/) :

```
sudo apt-get install lib32stdc++6 libcupsimage2:i386
```

It did not work yet and I found the line (in /var/log/cups/error_log) :

> D [08/Aug/2014:13:54:19 +0200] [Job 256] Dell-A920: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

However :

```

$ sudo apt-cache policy libstdc++5
libstdc++5:
  Installed: 1:3.3.6-25ubuntu4
  Candidate: 1:3.3.6-25ubuntu4
  Version table:
 *** 1:3.3.6-25ubuntu4 0
        500 http://be.archive.ubuntu.com/ubuntu/ trusty/universe amd64 Packages
        100 /var/lib/dpkg/status

```

So I concluded that the cups libary was looking for the i386 (32-bit) version of the library :

```

sudo apt-get install libstdc++5:i386

```

Now it works for me !

---

