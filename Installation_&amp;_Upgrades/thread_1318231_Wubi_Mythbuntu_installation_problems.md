---
title: "Wubi Mythbuntu installation problems"
date: 2009-11-07
forum: Installation &amp; Upgrades
---

### Post by andysummerskill on 2009-11-07
Just tried installing mythbuntu 9.10 using wubi on XP MCE system.

Used the mythbuntu-9.10-desktop-i386.iso image which was downloaded by wubi.

All seemed to be going OK until the 2nd reboot when I was presented with what appears to be a windows boot loader screen (had the 'press F8 for advanced windows options' comment) with the options:

        Microsoft Windows XP Professional Edition
        Microsoft Windows Recovery Console
        Mythbuntu

Selected Mythbuntu which opened the Grub Boot loader screen but here there was only the option to to start either:

        Windows NT/2000/XP (on /dev/sda1)
or     Microsoft Windows XP Professional Edition (on /dev/sda2)

Selecting either of these results in the error:

         error: unknown command 'drivemap'

I've checked the code for each selection:

        Insmod     fat
        Set root=(hd0,1) 
        search --no-floppy --fs-uuid --set 3371-05fe
        drivemap -s (hd0) ${root}
        chainloader +1

and

        Insmod     ntfs
        Set root=(hd0,2) 
        search --no-floppy --fs-uuid --set 10c8ccf7c8ccdc5a
        drivemap -s (hd0)  ${root}
        chainloader +1

FYI. My system is a HP windows MCE machine.
       Pentium4 2.93GHz CPU
       512MB RAM
       160GB IDE HDD (70GB Free)
       ATI Radeon Graphics Card
       Hauppague 150PVR(MCE Compatible) TV Card

Anyone help?

Regards,

Andy

---

### Post by mrand on 2009-12-17
For anyone running into this problem, appears there is a bug filed:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/477104)

---

### Post by Colin Keenan on 2010-02-11
I tried to read the "bug filed" link mentioned in the previous post, but don't understand if it's really the same problem.  Can't find mention of "unknown command 'drivemap'" error.

I'm brand new to Ubuntu Linux.  I did the installation using the Ubuntu Installer for Windows (wubi.exe) and installed Ubuntu 9.10.  It worked and right away upgraded.  Almost everything works very well and I'm very surprised that I like it better than either Windows or Mac because I had bad experiences with Redhat Linux back in the '90's.

Anyway, if I try to boot Windows XP Pro from grub, it just says

"error: unknown command 'drivemap'"

Searching this forum for "unknown command 'drivemap'" using the quotes to search on the full phrase, reveals this thread and a closed one from back in October when this problem was first noticed.

Most people probably don't complain because Windows has it's own boot screen that comes first and defaults to Windows so turning on the machine without pushing any buttons goes into Windows anyway so that there's no need to use grub to get into Windows.

Still, thought I should point out that this problem that was noticed back in October is still with us in January 2010.

---

### Post by Colin Keenan on 2010-02-11
Here is the correct bug report for this problem:

[https://bugs.launchpad.net/wubi/+bug/466745](https://bugs.launchpad.net/wubi/+bug/466745)

But why is the latest status for wubi set to invalid on this bug report?

---

