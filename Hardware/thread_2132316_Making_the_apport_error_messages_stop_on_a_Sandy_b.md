---
title: "Making the apport error messages stop on a Sandy bridge notebook"
date: 2013-04-04
forum: Hardware
---

### Post by ckop64 on 2013-04-04
Hello folks, I have a fresh install of Ubuntu 12.10 on my HP Pavilion G6-1315SH B1Y39EA. This particular notebook has an AMD HD7450M dedicated VGA card and one made by Intel. I've had two problems so far, both regarding the sandy bridge construction. 
I think I've got rid of the first one by putting ```
echo OFF > /sys/kernel/debug/vgaswitcheroo/switch
``` in my /etc/rc.local. This seems to have solved the overheating and the low battery life issues by turning off the dedicated graphics card, which honestly I don't need at all under Linux, but I have an other one that still persists. Namely I get these error reports every now and then, seemingly at random (see attachment).

My question is: is there a way to fix this error or at least to make the error messages stop? They get very disturbing after a while.
I don't know if this is relevant, but I haven't got these error messages during the installation, so I'm assuming a driver or a kernel issue.

Thanks for your help in advance. :)

---

### Post by ibjsb4 on 2013-04-04
You could disable apport.

[http://ubuntuforums.org/showthread.php?t=2053494](http://ubuntuforums.org/showthread.php?t=2053494)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+apport&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=disable+apport&sa=Search&cof=FORID:9)

---

### Post by ckop64 on 2013-04-04
Thanks for the workaround. Has this issue been identified yet?

---

### Post by ibjsb4 on 2013-04-04
Really don't know, I do not even have it installed :)

---

### Post by kjkrum on 2013-04-04
Similar problem here.  I have a Sandy Bridge Celeron in a Gigabyte GA-Z77-HD3.  The weird thing is, I am actually using the on-chip/on-board graphics.  There is no apparent crash.  Everything appears to be working perfectly, despite Apport's constant alarms.

---

### Post by ibjsb4 on 2013-04-04
Apport is not enabled by default in stable releases, even if it is installed. The automatic crash interception component of apport is disabled by default in stable releases for a number of reasons:

    Apport collects potentially sensitive data, such as core dumps, stack traces, and log files. They can contain passwords, credit card numbers, serial numbers, and other private material.

    This is mitigated by the fact that it presents you what will be sent to the bug tracker, and that all crash report bugs are private by default, limited to the Ubuntu bug triaging team. We can reasonably expect developers and technically savvy users, who run the development release, to be aware of this and judge whether it is appropriate to file a crash report. But we shouldn't assume that every Ubuntu user of stable releases is able to do so. In 12.04 and up this is transparently handled by whoopsie, see ErrorTracker.
    During the development release we already collect thousands of crash reports, much more than we can ever fix. Continuing to collect those for stable releases is not really useful, since
        The most important crashes have already been discovered in the development release.

        The less important ones are not suitable for getting fixed in stable releases (see [https://wiki.ubuntu.com/StableReleaseUpdates](https://wiki.ubuntu.com/StableReleaseUpdates)
        Asking users to send crash reports to us is insincere, since we can't possibly answer and deal with all of them. 
    Data collection from apport takes a nontrivial amount of CPU and I/O resources, which slow down the computer and don't allow you to restart the crashed program for several seconds. 

[https://wiki.ubuntu.com/Apport](https://wiki.ubuntu.com/Apport)

---

### Post by kjkrum on 2013-04-04
> **ibjsb4 said:**
> Apport is not **supposed to be** enabled by default in stable releases

FTFY.  I certainly did not intentionally enable it, but somehow it became enabled on my 12.04.2 system.

I don't remember exactly when I started seeing it.  Maybe two weeks ago.

I'm tempted to just disable it, but it would be nice to know why it thinks X is crashing.

---

### Post by ibjsb4 on 2013-04-04
I suspect a version upgrade enables it (12o4.1 to .2) and we just don't know it until it spits out a report.  Just my guess :)

---

### Post by ckop64 on 2013-04-05
Actually I am running a stable release, 12.10. Or did you mean LTS by stable?

---

### Post by kjkrum on 2013-04-16
I installed 12.04.02 on a brand new machine.  Maybe a package upgrade enabled it?

Does apport restart the crashed app?  Since disabling apport, X actually does appear to be crashing... which is far more annoying than the occasional error message.

---

### Post by roly33 on 2013-04-18
I had this just now after a re-boot from installing updates and my CPU is an Intel Celeron 900 with onboard Intel GM45 Graphics.

Roland

---

### Post by kjkrum on 2013-04-18
The common thread seems to be the use or presence of Intel onboard graphics.  And indeed, the error details I'm seeing in Apport refer to the Intel graphics kernel module.  But clicking "report" doesn't give me any feedback that it's actually been reported.  And I'm not sure how to see the actual error logs or messages so I could search for a solution.

---

