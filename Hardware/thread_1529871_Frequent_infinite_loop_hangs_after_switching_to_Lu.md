---
title: "Frequent infinite loop hangs after switching to Lucid on my netbook"
date: 2010-07-12
forum: Hardware
---

### Post by dkulchenko on 2010-07-12
After I did a clean-install of Lucid on my netbook (Jaunty was running fine previously), I tried to install a few CPAN (Perl) modules. During web server tests, my netbook would consistently hard lock (display stops changing, mouse and keyboard not responding, SysRq not responding, only option to shutdown is hold power button). I'm not sure if this is a kernel issue, a libc issue, or what (I'm fully updated as of today), but the problem is *only* present in Ubuntu 10.04 and Linux Mint 9 (and all other Ubuntu derivatives of the current version). Reinstalls did not fix the problem. Updating to upstream 2.6.34 does not fix the issue. However, the problem is *not* present in the current RC of openSUSE 13.0, in recent Mandriva, or in Fedora 13 (most recent) on the same hardware, which leads me to believe this is a Ubuntu issue, not an upstream kernel issue.

If I run the same commands from a tty, at the point where the display would usually hard lock, I suddenly get a huge barrage of [1234.somenumber] panic(0xblahblah) and similar messages scrolling by very quickly, in a loop, and I can do nothing, just hard shutdown. I took a few photos of those messages.

I'd really like to use Ubuntu, because it's lightyears ahead of everything else right now, but I'm currently stuck on using openSUSE (and I hate it). What can I do?

(My hardware details, some photos of the infinite loop messages, and the relevant bug report can be found at: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/599174](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/599174)). 

Thanks in advance!

---

