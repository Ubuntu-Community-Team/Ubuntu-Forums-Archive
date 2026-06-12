---
title: "Installing new kernel hardware fix"
date: 2009-04-19
forum: Hardware
---

### Post by theboozler on 2009-04-19
I have a Western Digital hard drive (WDC WD1600JS-62MHB5) and have been having problems with it ever since 8.04 (kernel 2.6.23ish). I have discovered the problem and have found a fix for it in another forum: [http://ubuntuforums.org/showthread.php?t=816500&page=6]("http://ubuntuforums.org/showthread.php?t=816500&page=6")

Basically this fix, or rather 'work around', only modifies the kernel's libata-core.c very slightly. Here is the kernel.org patch: [http://bugzilla.kernel.org/show_bug.cgi?id=11579]("http://bugzilla.kernel.org/show_bug.cgi?id=11579")

What I did was follow the instructions for downloading the Ubuntu kernel at [https://help.ubuntu.com/community/Kernel/Compile]("https://help.ubuntu.com/community/Kernel/Compile") and managed to MANUALLY edit the code (patch is for vanilla kernel), compile and install.

My question: is there an easier way to apply this fix for my machine in the future? Does libata-core.c compile into a module that I can now simply copy and paste over? I'm looking for some way to fix my problem without spending an hour+ recompiling for merely a dozen lines of code!

PS: My compile command was CONCURRENCY_LEVEL=2 AUTOBUILD=1 NOEXTRAS=1 fakeroot debian/rules binary-generic . Any way to speed this up?  All I need is one kernel for an amd64 desktop machine...

PPS: I don't know how the kernel patch and update system works with propagating to ubuntu, could I expect the vanilla kernel's patch/'work around' above to be included in future ubuntu updates? Or other distro's updates for that matter? If not I may just buy a new HD because this is all a major pain in the ***!

---

