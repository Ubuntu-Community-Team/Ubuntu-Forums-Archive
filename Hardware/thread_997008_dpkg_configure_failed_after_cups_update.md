---
title: "dpkg configure failed after cups update"
date: 2008-11-29
forum: Hardware
---

### Post by petzler on 2008-11-29
Hi,

on my Ubuntu (upgraded from 8.04.1 to 8.10) after the last dist-upgrade (apt-get dist-upgrade) yesterday I get errors on cups deb package.

```

root@tux:~# dpkg -l cups
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Cfg-files/Unpacked/Failed-cfg/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name                       Version                    Description
+++-==========================-==========================-====================================================================
rW  cups                       1.3.9-2ubuntu3             Common UNIX Printing System(tm) - server

```

```

root@tux:~# apt-get clean cups
root@tux:~# dpkg --configure cups
dpkg: error processing cups (--configure):
 package cups is not ready for configuration
 cannot configure (current status `triggers-awaited')
Errors were encountered while processing:
 cups
root@tux:~# dpkg -C     
The following packages are awaiting processing of triggers that they
have activated in other packages.  This processing can be requested using
dselect or dpkg --configure --pending (or dpkg --triggers-only):
 cups                 Common UNIX Printing System(tm) - server
root@tux:~# dpkg --triggers-only cups
dpkg: error processing cups (--triggers-only):
 package cups is not ready for trigger processing
 (current status `triggers-awaited' with no pending triggers)
Errors were encountered while processing:
 cups

```

The last entry is interesting, cups is awaitng triggers which are not pending, isn't it? I found an bug entry for man-db which seems to suffer from the same/similar problem but the work around did not help. Reinstall (or even remove) is not wise/possible:

```

root@tux:~# dpkg -r cups
dpkg: dependency problems prevent removal of cups:
 hplip depends on cups (>= 1.1.20).
 ubuntu-desktop depends on cups.
 kubuntu-desktop depends on cups.
 cups-driver-gutenprint depends on cups (>= 1.2.5) | cups (>= 1.2.5).
 cups-driver-gutenprint depends on cups (>= 1.2.5) | cups (>= 1.2.5).
 hal-cups-utils depends on cups.
 cups-pdf depends on cups (>= 1.1.15).
dpkg: error processing cups (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 cups

```

... the hole system is replaced. Any ideas what happens here? How to solve it?

Thanks,
Olaf

---

### Post by petzler on 2008-12-02
Well, since there are pending triggers I did try to reinstall cups-bsd only. Same/still problems. I'm alone with this here?

Regards,
Olaf

---

### Post by Jonne on 2009-01-31
I just have the same issue (partly my fault for running apt-get over ssh without using screen). Did you ever solve this without doing a full reinstall?

---

### Post by DSA on 2009-02-05
I seem to have a similar problem with 8.04.

After an update to CUPS, the printing stopped after some errors. The printers that I had set and running disappeared and I cannot access the localhost CUPS servers. I try to re-instal from the package manager but it fails.


Daniel

---

### Post by Jonne on 2009-02-05
I just reinstalled everything to solve the problem (which was relatively painless as my home dir is a seperate partition). I realize this isn't a proper solution, but it worked for me ;).

---

### Post by Jonne on 2009-02-05
[https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/323894](https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/323894)
The fix for this bug came as an update today, so either use the workaround in the bug report, or wait until the updated package comes down through update manager.

---

