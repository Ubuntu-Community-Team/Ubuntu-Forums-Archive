---
title: "SATA 1.0 VT6421 RAID Card Driver Incompatibility with Western Digital SATA 2.0 HD"
date: 2011-01-13
forum: Hardware
---

### Post by josephdpurcell@gmail.com on 2011-01-13
BRIEF:
======

The VT6421 chipset is incompatible with Western Digital hard drives under Ubuntu Linux, and any linux distrubtion.

INTRO:
======

I have worked on this issue for over a month now and it remains unresolved. The setup I am going for is on a P4 machine with an IDE master drive that will have the OS and two 500GB Western Digital WD5000AAKS Caviar Blue SATA 2.0 drives attached to a Via Technologies VT6421 SATA 1.0 PCI RAID card. The SATA 2.0 vs. SATA 1.0 can be overcome by putting pins on jumper #5 and #6 which makes the HDs operate at SATA 1.0. The PCI card claims to have the capacity for two independent ports, thus, instead of using whatever RAID capability the card has, I can setup my computer using Linux's software RAID. Having eliminated other possible factors, the issue I see is that the WD drives are having difficulty communicating with the VT6421 chipset under Linux (see [http://patchwork.ozlabs.org/patch/54101/](http://patchwork.ozlabs.org/patch/54101/) and [https://bugzilla.kernel.org/show_bug.cgi?id=15173](https://bugzilla.kernel.org/show_bug.cgi?id=15173)). It is strictly an OS issue as well, seeing that I was able to get it working with Windows XP. Note: attached is the most recent dmesg output using Ubuntu 10.10 and 2.6.37 kernel.

SYMPTOMS/THINGS I TRIED:
========================

1.) I would put an Ubuntu install disk in and it would freeze at random points if both drives were connected.

2.) I put in a GParted Live CD to format the drives and GParted would freeze--same happened when I used Knoppix.

3.) I would install Ubuntu (with various versions, even 10.10 with the 2.6.37 kernel upgrade) on the IDE drive with the two SATA drives unplugged, then reboot and the OS would not boot up. It would give errors such as:
>     ...
    [    0.000000] ACPI: BIOS age (1999) fails cutoff (2000), acpi=force is required to enable ACPI
    [    3.393186] IO APIC resources could be not allocated.
    ...
    [    9.091233] ata4.00: revalidation failed (errno=-5)
    ...
    [    41.519498] ata4.00: status: { DRDY ERR }
    [    41.519552] ata4.00: error: { ICRC ABRT }
    [    41.860481] ata4.00: exception Emask 0x12 SAct 0x0 SErr ox1380500 action 0x6
    [    41.860544] ata4.00: BMDMA stat 0x5
    [    41.860599] ata4: SError: { UnrecovData Proto 10B8B Dispar BadCRC TrStaTrns }
    ...
    Note: these may not be the same errors on each PC I used, I did try different PCs.Though I don't have the specifics, there were a number of times where I noticed key words like "freeze", "delay", and other words that signified unresponsiveness or latency; one of the errors said, "ata2: port is slow to respond, please be patient (Status 0xd1)".

4.) I began to experiment with having only 1 drive attached. I found that I was able to format, mount, and write to the drive. There may have been a few errors on startup, but nothing fatal. Then, I would plug in the other drive, format, mount, and write to it and it was fine. Then, when plugging both in at the same time the OS wouldn't boot.

5.) I finally decided that the driver CD that came with the card was not just to activate its RAID functionality, but to be able to even use the card. I wanted to make sure the card even worked, just to be extra sure, so I installed XP and the driver and bingo, it worked.

6.) So, I started looking for a Linux driver and found that Via Technologies has drivers: [http://www.via.com.tw/en/support/drivers.jsp](http://www.via.com.tw/en/support/drivers.jsp). However, their drivers are for IDE and they would not install anyway, I even tried different Linux distros. I would get errors like:
>     dpkg: error processing via-ide-patch (--install):
    subprocess post-installation script returned error exit status 1
    Errors were encountered while processing:
    via-ide-patch
    (See [http://forums.debian.net/viewtopic.php?f=7&t=50531](http://forums.debian.net/viewtopic.php?f=7&t=50531) for complete output of the error)So, they give you the source code with instructions to use it when compiling the kernel. I've never done that but thought I'd try it. After waiting an hour or so it errored out, there was some error in their C script about an integer vs. string issue. I gave up on that.

7.) So, I kept searching for information regarding the VT6421 chipset on linux and found a number of people who had issues, specifically the following two bugs:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422994](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422994)
[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/263160](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/263160)
Long story short, I found two patches in the change log for kernel 2.6.37 regarding fixing a sata_via issue:
> 
    commit 6656b3fc8aba2eb7ca00c06c7fe4917938b0b652
    Merge: 33e0d57 b1353e4
    Author: Linus Torvalds <torvalds@linux-foundation.org>
    Date:   Fri Nov 19 11:59:49 2010 -0800
    
        Merge branch 'upstream-linus' of git://git.kernel.org/pub/scm/linux/kernel/git/jgarzik/libata-dev
        
        * 'upstream-linus' of git://git.kernel.org/pub/scm/linux/kernel/git/jgarzik/libata-dev:
          sata_via: apply magic FIFO fix to vt6420 too

    AND

    commit b1353e4f40f6179ab26a3bb1b2e1fe29ffe534f5
    Author: Tejun Heo <tj@kernel.org>
    Date:   Fri Nov 19 15:29:19 2010 +0100
    
        sata_via: apply magic FIFO fix to vt6420 too
        
        vt6420 has the same FIFO overflow problem as vt6421 when combined with
        certain devices.  This patch applies the magic fix to vt6420 too.
        
        Signed-off-by: Tejun Heo <tj@kernel.org>
        Reported-by: Martin Qvist <q@maq.dk>
        Reported-by: Peter Zijlstra <peterz@infradead.org>
        Cc: Joseph Chan <JosephChan@via.com.tw>
        Cc: [EMAIL="stable@kernel.org"]stable@kernel.org[/EMAIL]
        Signed-off-by: Jeff Garzik <jgarzik@redhat.com>
That is when I started on a journey to update the kernel. If you've never compiled a kernel, it takes around 3-4 hours depending on your computer speed. After compiling, I installed, rebooted, and now it can't find the filesystem. So, I kept searching and found a miracle: [http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/](http://www.ramoonus.nl/2011/01/linux-kernel-2-6-37-installation-guide-for-ubuntu-linux/). You download and install the 3 deb packages there and you get kernel 2.6.37. I plug the two drives in, start it up, and it produces the same results. (Yes, if you know what insanity is--at this point I'm feeling insane.)

8.) Update: I installed Ubuntu Knatty 11.04 Alpha 1 and plugged in the two hard drives and the OS failed. I tried just booting with the live CD and it failed too.

ELIMINATED ISSUES:
==================

1.) I tried most of the above with a different RAID card, but I don't remember the details, but I had the same issues as I do now, so I don't think it's the card.

2.) I supposedly eliminated the SATA 1.0 vs. 2.0 compatibility issue by putting jumper pins on pins #5 and #6 on the drives which make the drives perform at 1.5Gbs, or SATA 1.0.

3.) I eliminated the possibility of having bad hard drives. I bought three of them, returned them for three more. Still same issues.

CONCLUSION:
===========

Unless I am doing something wrong, this issue has yet to be resolved by Linux kernel developers.

SEE ALSO:
=========

The following threads have been made on similar issues all with no solution:
[http://ubuntuforums.org/showthread.php?t=725736](http://ubuntuforums.org/showthread.php?t=725736)
[http://ubuntuforums.org/showthread.php?t=664517](http://ubuntuforums.org/showthread.php?t=664517)
[http://ubuntuforums.org/showthread.php?t=494872](http://ubuntuforums.org/showthread.php?t=494872)
[http://ubuntuforums.org/showthread.php?t=573945](http://ubuntuforums.org/showthread.php?t=573945)
[http://ubuntuforums.org/showthread.php?t=527441](http://ubuntuforums.org/showthread.php?t=527441)
[http://ubuntuforums.org/showthread.php?t=276797](http://ubuntuforums.org/showthread.php?t=276797)
[http://ubuntuforums.org/showthread.php?t=222585](http://ubuntuforums.org/showthread.php?t=222585)
[http://ubuntuforums.org/showthread.php?t=1318300](http://ubuntuforums.org/showthread.php?t=1318300)

People elsewhere who are having the same issues:
[http://doit.juii.net/uncategorized/1220](http://doit.juii.net/uncategorized/1220)
[http://www.viaarena.com/forums/showthread.php?t=35493](http://www.viaarena.com/forums/showthread.php?t=35493)
[https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/263160](https://bugs.launchpad.net/ubuntu/intrepid/+source/linux/+bug/263160)
[http://us.generation-nt.com/answer/patch-sata-via-enable-magic-transmission-fix-vt6420-help-201056501.html](http://us.generation-nt.com/answer/patch-sata-via-enable-magic-transmission-fix-vt6420-help-201056501.html)
[http://forums.fedoraforum.org/showthread.php?t=144494](http://forums.fedoraforum.org/showthread.php?t=144494)
[http://techblogbydave.blogspot.com/2007/05/via-vt6421-sata-card-does-job.html](http://techblogbydave.blogspot.com/2007/05/via-vt6421-sata-card-does-job.html)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344093](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/344093)

People who claim to have solution:
[http://csoinstitute.org/node/49523](http://csoinstitute.org/node/49523)
[http://boardreader.com/thread/Ubuntu_7_10_Gutsy_Gibbon_via_SATA_VT6421_cyvX1plc.html](http://boardreader.com/thread/Ubuntu_7_10_Gutsy_Gibbon_via_SATA_VT6421_cyvX1plc.html)
[http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/](http://kernelreloaded.blog385.com/index.php/archives/ubuntu-and-via-vt6421-pci-sata-howto/)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422994/comments/10](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422994/comments/10)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422994/comments/34](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422994/comments/34)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422994/comments/44](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422994/comments/44)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422994/comments/48](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/422994/comments/48)
[http://kerneltrap.org/mailarchive/git-commits-head/2010/6/3/41147](http://kerneltrap.org/mailarchive/git-commits-head/2010/6/3/41147)
(very technical) [http://patchwork.ozlabs.org/patch/54101/](http://patchwork.ozlabs.org/patch/54101/)
(very technical) [https://bugzilla.kernel.org/show_bug.cgi?id=15173](https://bugzilla.kernel.org/show_bug.cgi?id=15173)
(C script solution) [http://lxr.free-electrons.com/source/drivers/ata/sata_via.c#L579](http://lxr.free-electrons.com/source/drivers/ata/sata_via.c#L579)
[http://answerpot.com/showthread.php?921169-Re%3A+sata_via+hard+resetting+link+%2F+freeze%3A+exception+Emask+0x12+SAct+0x0+SErr+0x1000500+action+0x6]("http://answerpot.com/showthread.php?921169-Re%3A+sata_via+hard+resetting+link+%2F+freeze%3A+exception+Emask+0x12+SAct+0x0+SErr+0x1000500+action+0x6")
[http://us.generation-nt.com/answer/patch-sata-via-enable-magic-transmission-fix-vt6420-help-201056501.html](http://us.generation-nt.com/answer/patch-sata-via-enable-magic-transmission-fix-vt6420-help-201056501.html)

---

### Post by The Real Dave on 2011-03-29
Wow, that's a brilliantly comprehensive report o.O

I'm also suffering from the same problem, with two slightly different VT6421a cards. 

So far, I've had no success with Debian 5, and have had issues testing with Arch and newer FreeNAS versions.

0.7.x FreeNAS versions were able to detect and use the card, but resulted in a lock up.

I'll be trying it out with the latest Natty Daily Build, and will post back with results.

---

### Post by josephdpurcell@gmail.com on 2011-04-03
@The Real Dave, thanks! Please reply back, because I still haven't resolved this issue. And speaking of which, if anyone has any good suggestions for solving what I want to do with a $20-50 card of some sort, I'd love to hear!

---

### Post by The Real Dave on 2011-04-14
So far, no luck. Natty hasn't been able to use the card, as has Arch.

I've yet to try it under Windows, and have created a some sort of a solution, by transplanting the drive into another system. 

When things calm down in a week or so, I'll try more daily builds, and perhaps BSD.

---

### Post by arnuschky on 2011-09-07
Hey,

I have the same problem. I started a new bug report for this:
[https://bugs.launchpad.net/ubuntu/+source/linux-lts-backport-natty/+bug/843639](https://bugs.launchpad.net/ubuntu/+source/linux-lts-backport-natty/+bug/843639)

Cheers,
Arnuschky

---

