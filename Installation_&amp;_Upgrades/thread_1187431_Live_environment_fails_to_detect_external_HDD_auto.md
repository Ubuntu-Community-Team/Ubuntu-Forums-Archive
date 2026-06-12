---
title: "Live environment fails to detect external HDD automatically &amp; how to report the bug?"
date: 2009-06-14
forum: Installation &amp; Upgrades
---

### Post by Reiger on 2009-06-14
I know this is a bug in the Live Environment for the simple reason that trying to install Fedora Leonidas and Debian to that device Just Works. 

But when my internal harddisk finally failed (all it can do now it cause kernel panics and funny noises when left inside and booting from the external HDD, so I removed the internal one), I didn't want Fedora (I tried it, didn't like it). Then I tried a Debian testing snapshot I had collected; installed that just fine, booted it just fine (in much the same way that the kubuntu install I tried didn't), then updated it to the current state of affairs in Debian testing. It is behind the times compared to Jaunty (not to mention Karmic, which used to be booted off the now thoroughly defunct formerly internal HDD), so I decided to get myself a Jaunty live environment instead.

So far so good. It burned to disc without errors, and just to be on the safe side I let the live environment check itself for errors: it didn't report anything. Time to boot into the Live Environment: no external harddisk when I finally get to the desktop.

Checked: the external harddisk is firmly connected with the USB socket through the USB cable and certainly `turned on' (LED-indicator claims so anyway). Ah well, just unplug and plug the USB cable back in and all will be OK.

Finally, install the Live Environment. Takes a while but we get there (incidentally: the kubuntu live installer is a lot less polished compared to bigger brother ubuntu). Nevermind that, time to boot into the new system.

5 seconds to GRUB. Then 35 seconds of `indeterminate progress bar' (no self-filling bar, just a block shuttling back and forth): that's not right? A black page, light grey console font with a message: the kernel didn't find the root device. /dev/disk/by-uuid/[some string here] missing. That's not so strange: /dev/disk/by-uuid itself is missing (too), so no wonder that _this_ uuid is not there.

Now, the real kicker is that when I try to report any of this to launchpad I just can't find out where to report it to. I don't see a big sign "DON'T PANIC: See if it is a known issue here" in large friendly letters, nor am I able to satisfactorily pinpoint the issue which means that the nice and friendly but slightly obscure mechanism for searching bug reports won't help me much either. Tried "install" (I get WebDAV, apache and what not), tried ubiquity [but I am not at all sure whether the bug is in ubiquity] (a load of garbage + ubiquity). Tried "Live environment"... ehrm _what_? Searching for _live enviroment_ yields all packages helpfully listed in alphabetical order? Clearly someone here must be doing something wrong. Let's assume that someone is me.

---

