---
title: "Packard-Bell IMEDIA 1601 problems"
date: 2009-09-09
forum: Hardware
---

### Post by brianmc on 2009-09-09
I've got this machine and the Windows install was hosed, plus no install media and the restore partition corrupted. I managed a boot from a live CD of the current version of Ubuntu, checked I could get sound and networking, and did a full install. I've now got some odd problems with failure partway through the startup process, or a freeze/lockup not long after it's booted and logged into.

From the front of the box, there's the following details:
Packard Bell AMD Athlon XP3000+
On the back:
UTOW-QUA
MS WHQL No.: QUA 872433
Model: IMEDIA 1601

Here's what I can do to try and explain the issues:

From a warm start following reboot of Windows with the live CD in the boot process froze with a message about the hardware abstraction layer.

When cold-booted it starts up Ubuntu, but a short time later it just freezes. There's no indication why, and no way out of it. What I can get running in the time before it locks up seems to work fine.

I'd really appreciate suggestions on how to go about troubleshooting this one. The machine appears to have a couple of extra cards in it - including one for video/TV input. I've not opened up the box to identify these yet, but don't have a problem pulling them if needed - they were not in use at all.

---

### Post by brianmc on 2009-09-09
Just to update on this...

I pulled the two mystery cards from the machine, an ASUS TV/FM card and a mystery made-in-China modem.

There's still a plug-in graphics card being used instead of whatever is on the motherboard, but this seems to work okay.

The difference following pulling the two cards is that the machine got a lot further before it locked up. I got all updates downloaded, and partway through the install process before it froze.

As with prior to pulling the two cards, when it locks up you can't do anything. The mouse pointer still moves, but you can't click or drag anything. Another detail I noticed is that when its locked up the caps lock light on the keyboard can't be changed.

---

### Post by brianmc on 2009-09-09
I appear to have found a fix to my problem, but not a particularly good one.

In the BIOS I disabled APIC, this didn't make a difference - although from what I can find there may be something within Linux itself related to that.

The problem did go away when, again in the BIOS, I disabled the L2 cache. The really big downside to this is that the machine runs much, much slower.

---

### Post by brianmc on 2009-10-11
My changes above were not the required fix.

See [http://ubuntuforums.org/showthread.php?t=1280101](http://ubuntuforums.org/showthread.php?t=1280101)

This *may* be the fix, and if so I can turn back on all the cacheing and stuff.

---

