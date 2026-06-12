---
title: "Energy consumption in Oneiric"
date: 2011-10-14
forum: Hardware
---

### Post by clemmy on 2011-10-14
Hi,

I open this new thread because I just found a solution to the increased battery drain that I was experiencing since upgrading to Oneiric. I hope that other users eventually affected by the same problem may found this post useful.

Consider this thread as the continuation of the original discussion in Ubuntu+1 subforum ([link]("http://ubuntuforums.org/showthread.php?t=1855126")) that is now closed after the official release of Oneiric.

**Quick summury of old discussion:**
> On my laptop, as well as some other users' laptop, Oneiric was draining battery faster than Natty. For example my battery drain increased from ~11W to ~17W while web browsing in wi-fi. (With the standard configuration, just turning off the discrete card).

Applying some tweaks ([link]("http://ubuntuforums.org/showpost.php?p=11337515&postcount=25")) I was able to reduce drain to 13-15W.. somehow better, but still worse than Natty's 11W. And moreover natty reached those 11W without the need any tweaking! Other users had improved their situation installing jupiter, but niether them were able to reach natty's drain.

So, a solution was still to be found..

And now my new discovery..

At first I believed that this regression in battery drain was software related, and not kernel related.. but it turned out that I was wrong!

I just downgraded the kernel on my oneiric to 2.6.39 (got it [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/")) and now my laptop drains 9-11W depending on use.. Great!

**UPDATE 2011-10-15:** in comment [#7]("http://ubuntuforums.org/showpost.php?p=11346775&postcount=7") tista suggested a better fix! Downgrading the kernel is no more required! we just have to pass a tweak to the standard 3.0 kernel.

---

### Post by tista on 2011-10-14
@clemmy,

Thanks for your research... :P

Unfortunately I didn't make huge differences by using your scripts, but anyway you should keep up the great work for it!!

I suppose some reasons...
* my VAIO Z (VPCZ21AJ) has Core i5 2410 as standard voltage, 1920x1080 full-HD LCD, mobile SATA RAID controller, LightPeak docking bay and some other "expensive" modules. usually in past, these modules were not tested on ubuntu properly...

Just now I've seen the battery power "16 to 20W" averages with lowest brightness... but I didn't test downgraded kernel yet, since sandy-bridge must be run under 3.0 or higher. Although I know 3.0 series might have some issues for power saving. ;)

cheers.

---

### Post by fuduntu on 2011-10-14
> **clemmy said:**
> Hi,

I open this new thread because I just found a solution to the increased battery drain that I was experiencing since upgrading to Oneiric. I hope that other users eventually affected by the same problem may found this post useful.

Consider this thread as the continuation of the original discussion in Ubuntu+1 subforum ([link]("http://ubuntuforums.org/showthread.php?t=1855126")) that is now closed after the official release of Oneiric.

**Quick summury of old discussion:**


**And now my new discovery..**

At first I believed that this regression in battery drain was software related, and not kernel related.. but it turned out that I was wrong!

I just downgraded the kernel on my oneiric to 2.6.39 (got it [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.39-oneiric/")) and now my laptop drains 9-11W depending on use.. Great!

Sounds like you have the buggy BIOS problem.

Go back to the new kernel, and add pcie_aspm=force as a kernel option to grub.

---

### Post by lvanderree on 2011-10-14
Thanks clemmy,

I tried it:

installed the 2.6.39 kernel and after that installed the acpi_call module to be able to disable my radeon.

The 3.0 kernel I got down to 17W, with this 2.6.39 kernel I am now down to 13W!

I can also see the temperature of my system has been lowered from something above 55 degrees to something below 50!

I also tried the 3.0 kernel with the pcie_aspm=force option, but this does not lead to any lower consumption, so there probably has changed somewhat more with regard to power consumption between 2.6.39 and 3.0 except for aspm.

---

### Post by clemmy on 2011-10-14
> **fuduntu said:**
> Sounds like you have the buggy BIOS problem.

Go back to the new kernel, and add pcie_aspm=force as a kernel option to grub.
No, I had already tested that, my BIOS is not affected.. so forcing aspm does not help.

Moreover, if I'm not wrong, laptops with buggy pcie aspm should have increased drain starting with 2.6.38 kernel.. In my laptop battery drains begins with 3.0 kernel, both 2.6.38 and 2.6.39 are ok.


BTW, I've just tried out fuduntu, but I have the same splitted screen problem as lvanderree

---

### Post by fuduntu on 2011-10-14
> **clemmy said:**
> No, I had already tested that, my BIOS is not affected.. so forcing aspm does not help.

Moreover, if I'm not wrong, laptops with buggy pcie aspm should have increased drain starting with 2.6.38 kernel.. In my laptop battery drains begins with 3.0 kernel, both 2.6.38 and 2.6.39 are ok.


BTW, I've just tried out fuduntu, but I have the same splitted screen problem as lvanderree

There is a new version of xorg in our unstable repository.

---

### Post by tista on 2011-10-15
Guys,

If you guys have any "Sandy-bridge" i915 gen6, please give it a try:
```
i915.i915_enable_rc6=1
```

You could put it into your kernel parameters on grub... 

I could fix the power consumptions on battery from 20W to 10W!! :P
Today I didn't think we had to rollback kernel to 2.6.39 on sandy-bridge anymore.

cheers.

---

### Post by lvanderree on 2011-10-15
EXCELLENT!!!!!


I am now running 3.0 as well, with this kernel option and power consumption is somewhere around 10W

or according to powertop --calibrate outcome, it has changed from
16.7 t0 9,5W!!!!

Score:    5,6  (192371,1)
Guess:   16,7
Actual:   9,5


I tried all kind of distro's, like Mint, Arch, OpenSuse, Fedora, Fubuntu, but only Mint got close to an acceptable power consumpution, but nothing works as nice as Ubuntu, with the debian-package system and stable packages (or at least more stable than Mint)!

I was already thinking about using Windows again. I would of course run Ubuntu in a VM, but after more than 6 years of happily using Ubuntu and other Linux variants without Windows, this was a real painful moment! 

This solution definitely makes my day (or actually week, no month...s ;-))

How did you find this solution?

---

### Post by aeronutt on 2011-10-15
> **tista said:**
> Guys,

If you guys have any "Sandy-bridge" i915 gen6, please give it a try:
```
i915.i915_enable_rc6=1
```

You could put it into your kernel parameters on grub... 

I could fix the power consumptions on battery from 20W to 10W!! :P
Today I didn't think we had to rollback kernel to 2.6.39 on sandy-bridge anymore.

cheers.

How do I discover which gen SandyBridge I have? (Or, does this work for only gen6?)

---

### Post by aeronutt on 2011-10-15
> **tista said:**
> ... but I didn't test downgraded kernel yet, since sandy-bridge must be run under 3.0 or higher. ...

I'm running SB (i3) on a 2.x kernel (11.04) just fine.

---

### Post by fuduntu on 2011-10-15
FYI - [http://www.fuduntu.org/forum/viewtopic.php?p=6895#p6895](http://www.fuduntu.org/forum/viewtopic.php?p=6895#p6895)

Sandy Bridge Thinkpad, kernel 3.0.3 - 7.5 watts, 9.5 hours estimated battery life.. ;)

---

### Post by aeronutt on 2011-10-15
> **tista said:**
> Guys,

If you guys have any "Sandy-bridge" i915 gen6, please give it a try:
```
i915.i915_enable_rc6=1
```

You could put it into your kernel parameters on grub... 

I could fix the power consumptions on battery from 20W to 10W!! :P
Today I didn't think we had to rollback kernel to 2.6.39 on sandy-bridge anymore.

cheers.

BINGO!!  Using this, my current drain went from 1500mA to 900mA.  Now, it's at the same level as in my 11.04 install. 

Exactly what does this kernel option do?

---

### Post by lvanderree on 2011-10-15
apparently there are some more options, you can read all about them at this site:

[http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_i915_power&num=1)

---

### Post by tista on 2011-10-15
Guys,

See this patch:
[http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-oneiric.git;a=blobdiff;f=drivers/gpu/drm/i915/i915_drv.c;h=eb91e2dd791495ed5f40575a4f2190a0b8ad276c;hp=58222e86e2914710389c45bb796c2751d1f4d671;hb=05bd42688dbc066d4e2689b6f73c0470601f788b;hpb=a7b85d2aa63ed09cd5a4a640772b3272f5ac7caa]("http://kernel.ubuntu.com/git?p=ubuntu/ubuntu-oneiric.git;a=blobdiff;f=drivers/gpu/drm/i915/i915_drv.c;h=eb91e2dd791495ed5f40575a4f2190a0b8ad276c;hp=58222e86e2914710389c45bb796c2751d1f4d671;hb=05bd42688dbc066d4e2689b6f73c0470601f788b;hpb=a7b85d2aa63ed09cd5a4a640772b3272f5ac7caa")

Yeah Ubuntu applied this patch from 3.0.0-7, then our sandy-bridge could not enable new generation drm features as default... :S
I didn't track this codes down yet especially drm/i915, but maybe it would be acceptable.

But this kernel parameters might be caused issues on some minor i915 models, something like graphics corruptions or so, I suppose that patch could be a workaround for that,,,

Anyway, a lot of PC employed Sandy-Bridge released around 2011 or higher could accept this "re-enabling rc6" I hope. ;)

regards.

---

### Post by Attila_fdd on 2011-10-15
and what about who got an older i3 330? :)

My laptop suffer of lower battery life after upgrading to ubuntu 11.10. Do you have any suggestion?

---

### Post by tista on 2011-10-15
> **Attila_fdd said:**
> and what about who got an older i3 330? :)

My laptop suffer of lower battery life after upgrading to ubuntu 11.10. Do you have any suggestion?

Hi,

OK...
If this output says 8086 or higher PCI-id model, it would be OK to apply that fix:
```
lspci -nv | grep VGA
```

cheers.

---

### Post by clemmy on 2011-10-15
> **tista said:**
> Guys,

If you guys have any "Sandy-bridge" i915 gen6, please give it a try:
```
i915.i915_enable_rc6=1
```

You could put it into your kernel parameters on grub... 

I could fix the power consumptions on battery from 20W to 10W!! :P
Today I didn't think we had to rollback kernel to 2.6.39 on sandy-bridge anymore.

cheers.
Thanks a lot! It works great on my system! I'm web browsing (via wi-fi) for some 15 minutes to test, and the drain rate it's always between 8.5W and 12W.. with 9 - 9.5W being the most frequent!

---

### Post by clemmy on 2011-10-15
> **fuduntu said:**
> FYI - [http://www.fuduntu.org/forum/viewtopic.php?p=6895#p6895](http://www.fuduntu.org/forum/viewtopic.php?p=6895#p6895)

Sandy Bridge Thinkpad, kernel 3.0.3 - 7.5 watts, 9.5 hours estimated battery life.. ;)

Seems good! For sere I'll give it a try next week.. even if I admit that I won't be easy to make me switch distribution: I appreciate the new unity interface, and I really like the me-menu..

---

### Post by joee92 on 2011-11-07
Thanks tista.  This has reduced the power consumption of my ThinkPad X220 from about 20W to about 14W (at max screen brightness).

Is there a way to do this in /etc/modprobe.d/i915.conf?  I tried this, but it didn't seem to work:

```
options i915 i915_enable_rc6=1
```

---

### Post by acutbal on 2011-11-08
Hello, I have an HP-G62 with AMD Phenom II N620 Dual-Core Processor, a dual GPU ATI Mobility Radeon HD 5470 and HD 4250 and 4Gb RAM, Ubuntu 11.10+GnomeShell installed. I only have 1.5 hours estimated battery life. I think it isn't normal if when in W7 battery lives about 3 hours minimum. Do you have any suggestion?

---

