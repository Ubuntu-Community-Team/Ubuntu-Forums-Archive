---
title: "Special key &lt;fn up-arrow&gt; crashes X server on Inspiron 9400, Edgy i386, NVIDIA 7900GS"
date: 2007-01-17
forum: Hardware &amp; Laptops
---

### Post by gracin on 2007-01-17
Hello!

Strange problem on my Inspiron 9400 running 32-bit Edgy.  All special keys (that is, fn combinations) work nicely except <Fn-up arrow> for increasing the brightness of the screen.  Pressing Fn up arrow crashes X server with signal 11 every time.  Here's a log from X server, including the backtrace in the end:

X Window System Version 7.1.1
Release Date: 12 May 2006
X Protocol Version 11, Revision 0, Release 7.1.1
Build Operating System: Linux 2.6.15.7 i686 
Current Operating System: Linux vega 2.6.17-10-generic #2 SMP Tue Dec 5 22:28:26 UTC 
2006 i686
Build Date: 07 July 2006
        Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Tue Jan 16 13:19:26 2007
(==) Using config file: "/etc/X11/xorg.conf"
error opening security policy file /usr/lib/xserver/SecurityPolicy
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete" };
    xkb_symbols              { include "pc(pc105)+us+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
The XKEYBOARD keymap compiler (xkbcomp) reports:
> Warning:          Type "ONE_LEVEL" has 1 levels, but <RALT> has 2 symbols
>                   Ignoring extra symbols
Errors from xkbcomp are not fatal to the X server
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Error opening /dev/wacom : Invalid argument
(EE) xf86OpenSerial: Cannot open device /dev/wacom
        No such file or directory.
Synaptics DeviceInit called
SynapticsCtrl called.
Synaptics DeviceOn called
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

Backtrace:
0: X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /lib/tls/i686/cmov/libc.so.6(__strtoul_internal+0x3f) [0xb7d867df]
3: X [0x80e5a27]
4: X(xf86HandlePMEvents+0x3b) [0x80d264b]
5: X(xf86Wakeup+0x153) [0x80c4e23]
6: X(WakeupHandler+0x59) [0x808a5c9]
7: X(WaitForSomething+0x1b9) [0x81944f9]
8: X(Dispatch+0x82) [0x8086832]
9: X(main+0x485) [0x806e715]
10: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d6e8cc]
11: X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting

---

### Post by gracin on 2007-01-17
I've just tried adding -noacpi to X server and it does stop it from crashing, but it doesn't make the brightness keys functional.  Pressing fn-up and fn-down doesn't change anything.

---

### Post by ishmeetahuja on 2007-02-12
hey i figured that out with the help of some extensive findings on the internet.

Atleast it started working on my system

[https://bugs.launchpad.net/distros/u....17/+bug/74284](https://bugs.launchpad.net/distros/u....17/+bug/74284) gives a way to solve this issue.

1. open and edit the file /etc/modprobe.d/blacklist

2. Append "blacklist video" at the end of the file.

3.Reboot

I was able to regain brightness control on my [B][B]Dell Inspiron 6400.
[/B][/B]
Try it out and wish u a good luck.

---

### Post by gracin on 2007-02-22
That solved the problem!  Thanks!!  I just have to figure out what is it that we lose by not including that module.  Everything seems to be working as before.

Thanks again for your help!

---

