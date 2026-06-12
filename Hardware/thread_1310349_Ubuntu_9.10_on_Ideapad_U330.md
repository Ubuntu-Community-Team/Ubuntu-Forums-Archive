---
title: "Ubuntu 9.10 on Ideapad U330"
date: 2009-11-01
forum: Hardware
---

### Post by ragad3 on 2009-11-01
Newbie to the forums, and a fan of Ubuntu... My level of Linux experience is intermediate.

I had no problems with the graphics when I installed 9.04 (Jaunty) on my Lenovo IdeaPad U330 - all went well, though the GUI was noticeably slow.

Now that Karmic has been released, I installed it from the Live CD, everything went well during the installation, but when I rebooted my laptop, I was asked to login through tty1 (no GUI). When I tried startx, it gives a lot of output on the screen (I named my machine 'performance'):

```
X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-23-server i686 Ubuntu
Current Operating System: Linux performance 2.6.31-14-generic #48-Ubuntu SMP Fri Oct 16 14:04:26 UTC 2009 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-14-generic root=UUID=230ae85c-df4b-4b97-b8e4-8fc91e94f1fd ro quiet splash
Build Date: 26 October 2009  05:15:02PM
xorg-server 2:1.6.4-2ubuntu4 (buildd@)
    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
    to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xord.0.log", Time: Sun Nov  1 16:24:14 2009
(==) Using config file: "/etc/X11/xorg.conf"

(EE) Failed to load module "fglrx" (module does not exist, 0)
(EE) No drivers available.

Fatal server error:
no screens found

Please consult the The X.Org Foundation support
         at [http://wiki.x.org](http://wiki.x.org)
 for help.
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log
giving up.
xinit: No such file or directory (errno 2): unable to connect to X server
xinit: No such process (errno 3): Server error.
```

PLEASE HELP ME! In my BIOS for graphics, there are two options - discrete graphics and switchable graphics - I used discrete graphics and got the above problem. With switchable graphics, I am hardly able to login to tty1 - the screen keeps constantly flickering and I cannot enter anything coherently. I don't know what seems to be the problem... is the ATI fglrx driver missing? I installed it first in the Live Session, before installing ubuntu (it prompted me with the "Restricted Drivers Available" option first.

---

### Post by ragad3 on 2009-11-01
I got it fixed. I just reinstalled, this time, without installing the ATI driver during the Live Session. And it works! Like a charm! I think it got the drivers confused, as any driver installation done during the Live Session would have been on the RAM and not copied to disk! Great!

---

