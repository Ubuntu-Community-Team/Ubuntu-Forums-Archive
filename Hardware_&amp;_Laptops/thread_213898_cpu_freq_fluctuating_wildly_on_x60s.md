---
title: "cpu freq fluctuating wildly on x60s"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by geos2 on 2006-07-11
I just installed Dapper 6.06 LTS on a L2300 x60s, i have the 686-SMP kernel but the user experience is really choppy/slow.  When I look at Gkrellm i see the cpu frequency fluctuating between 1.5Ghz and 32Mhz.  

To make matters worse, I have sysfs tools installed and sysfs.conf set to use governor 'userspace' and what I assume would be a fixed frequency.  in addition cpufreq-info, gkrellm, and the cpu frequency applet give differing info about what the cpu frequency actually is...

Is there some link explaining just how CPU scaling is supposed to work in Ubuntu?   Changing the governors with cpufreq-set or sysfs.conf appears to have zero affect on what gkrellm says is going on (and doesn't fix the choppiness.) 

Thanks.

---

### Post by Seq on 2006-07-11
Do you happen to have powernowd running? This is a userspace scaling daemon that (I believe) is installed by default.

---

### Post by Hellkeepa on 2006-07-12
HELLo!

I think you'll find this thread very enlightening:
[http://ubuntuforums.org/showthread.php?t=204100](http://ubuntuforums.org/showthread.php?t=204100)

Happy codin'!

---

### Post by geos2 on 2006-07-12
Switching to the 386 single proc kernel seems to fix the choppiness, although the Gkrellm cpu frequency meter is still fluctuating so I guess that is a red herring.  

I guess I'm even more confused about what the problem actually is... I think I probably misconfigured something.

---

### Post by Hellkeepa on 2006-07-13
HELLo!

Hmmm.. I seem to recall something about a tool (I think it was gkrellm) fetching the CPU freq from the wrong place, thus displaying the wrong status. Whereas the "CPU Frequncy Monitor" applet always displays the correct one.
I'd check that one, and see what it tells you. If it shows a stable freq under idle then I'd say it's OK, and there's probably no misconfiguration from your side.

I've also updated the thread I linked to above, with some new information concerning the kernel they released yesterday.

Happy codin'!

---

### Post by geos2 on 2006-07-13
Well, unfortunately, I have a Core Duo system and wouldn't mind using a SMP-enabled kernel.

The system monitor shows the processor(s) stepping between 1Ghz and the max 1.5Ghz. But the computer is basically unusable with the 686-SMP kernel: I can barely type. With the 386 kernel it is usable but still drags.  

I think I'm heading towards a clean system install and seeing what happens.

---

### Post by geos2 on 2006-07-13
I seem to have fixed the choppiness issue, you see, with the x60s the system will hang for 5 minutes when it tries to mount the root file system during boot.  You can fix this by switching in BIOS the SATA mode from AHCI to Compatibility... but when i switched back to AHCI the choppiness went away.  I didn't see abnormal drive activity so I'm not sure what actually was happening...

---

### Post by geos2 on 2006-07-13
i take it back.  problem not fixed.  very frustrated. booting up from a shutdown it was fine for awhile and then at some unknown it became 'choppy' again.  there is no disk activity, no cpu hogging process. every cpu meter (except gkrellm) shows the cpu's are running normally, yet when I launch an application the little gnome animation of boxes moving, i can see each individual box as it moves out.  then, typing is a chore with extreme lag...

argh.

---

### Post by 0MG on 2006-07-15
I'm having the same type of problem on an Averatec 4150 w/AMD Turion64 1.6Ghz. It will constantly fluctuate back and forth between 1.6 Ghz and 800 Mhz without provocation.

Just to clarify I am running dapper x86

---

### Post by Hellkeepa on 2006-07-16
HELLo!

**OMG**: What kernel are you running? If you don't know you can find this out by typing "uname -srv" in the terminal. If this is a -686 kernel, and the version number is less than 2.6.15-26, then try to upgrade it or run the -386 kernel.
I refer to the link in my post above.

**geos2**: I've found that the "hanging while mounting root system" only happens when the power is plugged in at that point. If you unplug it just before getting to that point, and plug it in again at first sign of HDD-activity, then it won't hang.
Just a work-around though, but it points towards some ACPI settings for "powered" status being the problem.

Happy codin'!

---

### Post by geos2 on 2006-07-16
interesting, when i reported the 'hanging' problem as a bug on launchpad Ben Collins claimed it was fixed...  which it isn't with 2.15.26-686 at least...

---

