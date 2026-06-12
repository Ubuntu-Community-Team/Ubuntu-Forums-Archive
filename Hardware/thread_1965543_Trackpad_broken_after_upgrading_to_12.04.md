---
title: "Trackpad broken after upgrading to 12.04"
date: 2012-04-25
forum: Hardware
---

### Post by dankdave on 2012-04-25
Hey all,

I recently upgraded my Acer Aspire One 532h from 11.10 to 12.04 (precise).  After the upgrade, my mouse no longer works.  No clicking, no motion, nothing.  I can get to a terminal with keyboard shortcuts, but have no idea where to start with fixing this issue.

Any ideas about where to start?

Thanks in advance.

> uname -a:

Linux 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 i686 i386 GNU/Linux

> lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 12.04 LTS
Release:        12.04
Codename:   precise

---

### Post by dankdave on 2012-04-25
I should point out that xinput returns the following line:

xinput list

Virtual core pointer  id=2 [master pointer (3)]
Virtural corse XTEST pointer id=4 [slave pointer (2)]
SynPS/2 Synaptics TouchPad id=12 [slave pointer (2)]

...

and them some other output.

---

### Post by dankdave on 2012-04-26
Uhm ... I feel really stupid now.  If possible, this thread should be completely deleted.

Pressing Fn + F7 reenabled the touchpad.  (There's a little icon with a hand and a square, apparently this is the touchpad).  I had never used that combination in the past, perhaps the latest release added this keyboard combination as an option?

In the past, i.e. pre 10.10, my wireless card would sometimes get shut off if the computer was booted into Windows.  The only way I had to fix it, (Fn + F2 wouldn't work at the time) was to boot back into windows, and use that keyboard combination to turn it back on, and then reboot into linux.

At any rate, this thread should probably be deleted.

---

