---
title: "NTFS partition crash"
date: 2008-08-21
forum: General Help
---

### Post by amaged on 2008-08-21
Hello,

I am dual booting Gusty with XP and it has always worked till yesterday i was mounting my NTFS part. from Linux and it did mount but i was unable to access some folders, they gave me Input/Ouput error msg so I rebooted into Windows and it didnt work, right after GRUB, i get an error 'hardisk read error" so i boot into Linux and its working fine, this time if i try to mount it (/dev/sda1) I get:

 Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation

So i got a Windows install CD and i booted from it and pressed R to go to recovery console and it says that it cant find a hard drive while Linux can see it fine.

What can i do here, i dont want to loose my data and i dont think that its a hardware failure, looks like something messed up the NTFS journal or something.

Please help.

Regards,
Ahmed

---

### Post by coffeecat on 2008-08-21
Have you tried booting into Windows (on the hard drive - not the Windows CD) and:

> In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important!

?

---

### Post by amaged on 2008-08-21
Of course, when i pick Windows XP from my GRUB, i get a Harddrive read error, press cntrl+alt+del.

My situation now is that i cant even boot into windows to do chkdsk, the XP CD i have couldnt read that there is a harddisk there and o i couldnt get to the recovery console to run chkdsk.

How can i run chkdsk, is there any bootable CD that will allow me to do that?

Please help.

---

### Post by coffeecat on 2008-08-21
> **amaged said:**
> Of course, when i pick Windows XP from my GRUB, i get a Harddrive read error, press cntrl+alt+del.

My apologies; I misunderstood your first post.

All I can suggest is a last resort. See if anyone else has a better idea first.

In Ubuntu, install the package 'ntfsprogs' if it isn't installed already. Then try running 'ntfsfix' to see if it can make your Windows C: partition at least bootable, or at the very least visible to the Windows CD repair console. Read man ntfsfix first, but here it is anyway:

> NAME
       ntfsfix - fix common errors and force Windows to check NTFS

SYNOPSIS
       ntfsfix [options] device

DESCRIPTION
       ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.

       You may run ntfsfix on an NTFS volume if you think it  was  damaged  by
       Windows or some other way and it cannot be mounted.

OPTIONS
       Below is a summary of all the options that ntfsfix accepts.  Nearly all
       options have two equivalent names.  The short name is preceded by - and
       the long name is preceded by --.  Any single letter options, that don’t
       take an argument, can be combined into a single command, e.g.   -fv  is
       equivalent  to  -f  -v.   Long  named options can be abbreviated to any
 unique prefix of their name.

       -h, --help
              Show a list of options with a brief description of each one.

       -V, --version
              Show the version number, copyright and license

BUGS
       There are no known problems with ntfsfix.  If you  find  a  bug  please
       send an email describing the problem to the development team:
       [EMAIL="linux-ntfs-dev@lists.sourceforge.net"]linux-ntfs-dev@lists.sourceforge.net[/EMAIL]

AUTHORS
       ntfsfix  was written by Anton Altaparmakov, with contributions from Sz&#8208;
       abolcs Szakacsits.

AVAILABILITY
       ntfsfix is part of the ntfsprogs package and is available from:
       [http://www.linux-ntfs.org/content/view/19/37](http://www.linux-ntfs.org/content/view/19/37)
 unique prefix of their name.

       The manual pages are available online at:
       [http://man.linux-ntfs.org/](http://man.linux-ntfs.org/)

SEE ALSO[noparse]
       mkntfs(8), ntfsprogs(8)[/noparse]Warning - I have never tried this, and it may make a bad situation worse. Wait for more advice before you try it.

---

