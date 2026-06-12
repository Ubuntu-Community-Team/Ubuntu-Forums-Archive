---
title: "memtest86+ fail at [Random number sequence]"
date: 2012-11-30
forum: Hardware
---

### Post by andy_blah on 2012-11-30
[CENTER][IMG]http://i.imgur.com/QN6eT.png[/IMG][/CENTER]

I recently bought a RAM stick (1GB, PC2700, DDR1) was second-hand and as always it's good to check if they're actually in good working condition. Plugged in it worked fine, so I decided to run memtest86+ on it. It went well until at WallTime of 16:41 and at the 7th test (as in the snapshot above) it started spouting up a myriad of errors.
I've read somewhere that this is a common bug in this version of Memtest86+ and it manifests at roughly same test, same time and exactly same error address and size (129MB). So I ask you now, what should I do next to further diagnose?

---

### Post by 2F4U on 2012-11-30
Well, I don't know. In my experience, if memtest shows an error, there is something wrong with the RAM. The version you are using seems to be the latest available, so using a newer one where the potential bug is fixed seems out of question. It may be possible to use an older version of memtest and see how this version behaves.
I guess there are only two options available, either you trust the chip since the error shows up only at the seventh iteration, or you distrust the chip and don't use it.

---

### Post by andy_blah on 2012-11-30
Some people that confronted this "false positive" said they had the timings or BIOS settings wrong and the errors stopped showing up. The question is what exactly should I change.

Also I'm not disproving the results of the test. It just seems weird how the errors show up right at the beginning of the test, when you would expect it to happen at least a few % afterwards. Also I wanted to le the test continue but all it did was to show random addresses and add more errors for over 10 minutes.

I'll try later to do a test with an older version.

---

### Post by AKADAP on 2012-12-05
I am dealing with exactly this problem right now.

Both memory sticks I have report this exact error at exactly the same locations when I run them individually, or togather.

But ONLY if I am running memtest86+ 4.20 that came with the ubuntu or kbuntu live CD. It also eventually halted with an unexpected interrupt on this version

When I ran the version I downloaded  directly from [http://www.memtest.org/](http://www.memtest.org/) (precompiled CD-ROM image memtest86+ 4.20 iso) it ran through without errors.

There is also a beta version of memtest 5.00 beta1 available here: [http://forum.canardpc.com/threads/68001-Memtest86-5.00-Beta-available-!-Need-betatesters-](http://forum.canardpc.com/threads/68001-Memtest86-5.00-Beta-available-!-Need-betatesters-)! that also runs through without errors.

Kbuntu was unstable on this machine (why I was running memtest in the first place), but I'm beginning to believe that they chose compile time options that are incompatible with this AMD-64 processor/motherboard, not a hardware issue. This system ran windows 2000 for years without issues.

I need to let it run multiple passes (I've only let it run 1 pass on the official 4.2 and the beta so far) to be sure though.

I have tried many times with the Ubuntu version and had it fail instantly on test 7 with millions (literally, reports every address for 129 MB to 1919 MB) of errors every time. I even tried the slowest clock speed and slowest timing.

The odd thing is, in test 7 it appears it does not write to ram, the read values reported in errors match the patterns written in test 6.

---

### Post by AKADAP on 2012-12-05
20 hours running memtest86+ 5.00 beta 1 with no errors on a system that fails instantly on test 7 of the memtest86+ 4.20 that came with ubuntu.
Bought some new memory, behaves exactly the same as the old memory.

---

### Post by sirkubax on 2012-12-08
Hello

I can confirm, that memtest v4.20 is corrupted.
Mine version 4.20 is from Ubuntu 12.10 32bit iso.

I have tested memory on 2 different computers (Core 2 duo family , P4), 5 different memory chips - all of them are faulty starting from 129 mb, Random number test.

I did the same test with Memtest v2.11 and memory is ok.

Btw, v 2.11 report progress up to 105%

---

### Post by cdac on 2012-12-09
I was testing my failed system using memtest 4.2 bundled with Kubuntu 12.10, and I got the exactly same problem.
I am pretty sure that the bundled memtest is faulty.

---

### Post by ironclaw on 2012-12-09
This is a [known bug]("https://bugs.launchpad.net/ubuntu/+source/memtest86+/+bug/1071209") with the Memtest86+ distributed with Ubuntu 12.10. I have added some more details to [this answer]("http://superuser.com/a/517093/91193") on Super User.

---

