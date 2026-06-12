---
title: "Ryzen 7 Freezes"
date: 2018-05-07
forum: Hardware
---

### Post by hamiljf on 2018-05-07
A number of threads exist on this issue, but in other forums.  My (new, untuned) system includes:
AMD Ryzen 7 1700X 8 core running at 3.4G
ASUS Prime X370 Pro bios v 3203
GeForce GTX 1050 
16.04.1-Ubuntu SMP Thu Apr 5 16:43:10 UTC 2018
kernel 4.13.0-39-generic

The symptom is intermittent freezes usually under idle load.  Sometimes the mouse moves but the system is unresponsive, sometimes the clock stops, sometimes the system freezes at the moment one tries to use it.  Solutions have been proposed in various places, involving such things as re-organising (or disabling) IOMMU, rebuilding the kernel with different flags, disabling C6 state, adjusting voltages, and many other ideas, some of which have subsequently been found ineffective by their proponents.

Please would someone who really understands what is going wrong post an explanation, and if possible, some kind of 'authorised' solution.

If the problem really has been solved in 18.04, that would also be nice to know.

---

### Post by rniee on 2018-05-15
The Ryzen soft lockup bug has existed since Ryzen launched and affects the new 2000 series. AMD has ignored the issue so no idea if it is even being worked on.

You can track the bugs status on [AMDs forum]("https://community.amd.com/thread/225795") as well as [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1690085") and [bugzilla]("https://bugzilla.kernel.org/show_bug.cgi?id=196683")

It looks like other users have narrowed the problem to C6 low power states. I believe you need to disable C6 power states in your BIOS, that is if there is an option provided by your board. The downside being your processor will use more power when idle.

Reading through bugzilla I found this comment

           > Matthew Vaughn                                                  2018-05-04 04:51:28 UTC
I'm testing with just the 'Typical Current Idle' option and no other countermeasures enabled right now. I'll give it 24 hours before I'm convinced, given the frequency of previously observed lockups. So far, there have been none since my last comment, which is longer than any previous uptime interval I've had on this hardware since installing it.

For what it's worth, the 'auto' option for the current idle setting is no good. That's the default, and was the setting in effect when I was observing lockups.

           > Matthew Vaughn                                                  2018-05-05 02:25:59 UTC
24 hours of uptime without a lockup after only setting "typical current idle." Considering my rig had been locking up after very short uptimes without this setting, I'd say that's a significant difference.

---

