---
title: "Dell Inspiron 17R-SE 7720, fan problem"
date: 2013-12-17
forum: Hardware
---

### Post by jtownsle on 2013-12-17
There are hundreds of posts about the Dell fan/overheating issue on Google, and I've seen a couple here on the forums, but I thought I would see if there is an update, since the conclusion so far seems to be that the problem has not been solved.  I have a Dell Inspiron 17R-SE, 7720; x64, with an Intel 3rd Gen Core GPU, and NVidia GK107M [GeForce GT 650M].  
I recently made the leap from Windows 8 (which is the devil, forced on me by the manufacturer) to Linux.  After fighting with Linux Mint for 2 weeks unsuccessfully, I switched to pure Ubuntu--this fixed some of my problems, but not all.  The remaining problem is that the fan goes full speed all the time.  The only certified Ubuntu for a model close to mine is Precise, 12.04, which is what I installed, and I can't find any evidence that later versions have fixed the problem.  I have the latest Bios (A16) and drivers (as of Dec 10), and linux kernel 3.2.0-57.  
Solutions I have tried with no success:
Installing Bumblebee and bbswitch.  I have verified that bbswitch load_state=0 and the Nvidia card is off.  It did not impact the fan speed at all.
I installed i8k, which indeed does control the fan speed.  However, the problem doesn't seem to be an out of control fan, but heat--since it revs up then revs down over and over constantly.  
I installed pcsensor to check the temperatures, and indeed, the temperatures go up when the fan goes down, then the fan shoots up, then temps go back down.  So the fan is doing its job, seeming to indicate an actual overheating problem.
I tried pasting all 3 of the following into grub with no effect:
 i915.i915_enable_rc6=1i915.i915_enable_fbc=1i915.lvds_downclock=1
I have pasting the following into grub also with no effect:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash pci=noacpi pcie_aspm=force"
I hate the thought of going back to Windows, but I also don't want to damage my laptop from continually running hot, plus the fact it has but my battery life in half.
Here is an example of the bumblebee procedure I used, under "fan", although when this didn't work I found and tried several variations.  Again, i verified that bbswitch had successfully turned off the Nvidia card.[http://www.geek-tips.com/2013/08/08/ubuntu-13-04-on-the-dell-inspiron-17r-special-edition/I](http://www.geek-tips.com/2013/08/08/ubuntu-13-04-on-the-dell-inspiron-17r-special-edition/I)
 haven't tried it in Ubuntu, but in Mint I tried installing the latest Nvidia drivers they have published for Linux (331.20), and it put me into a very low-graphics screen that I couldn't get fixed, which is why I finall scrapped Mint to switch to Ubuntu, and I haven't tried the Nvidia drivers again.Any success stories on a Dell 17R-SE (7720) getting the fan/heat under control?

---

### Post by mörgæs on 2013-12-17
Hi, welcome to the fora.

> **jtownsle said:**
> and I can't find any evidence that later versions have fixed the problem.

- but have you tried installing 13.10? For such new hardware I would begin with the newest software.

---

### Post by jtownsle on 2013-12-17
> **mörgæs said:**
> have you tried installing 13.10? For such new hardware I would begin with the newest software.
Thanks for the response!  I haven't tried a newer build, since 12.04 is what is Ubuntu-certified for this Dell (actually my Dell is a slight model up, the 17R-SE, 7720, not the 7110 listed here, but this is the closest)---I presumed the one that is certified would have the best chance of working.  As I looked through the various fixes, I saw people who had installed 13.10 who claimed to have the same problem unresolved, while they also said that upgrading broke some of the things that were working in 12.04, like speakers that stopped working, wifi problems, etc.  On the other hand, if there's no way to get the fan under control, it's certainly an option if my alternative is scrap it and go back to Windows. <p>
[http://www.ubuntu.com/certification/hardware/201101-6957/](http://www.ubuntu.com/certification/hardware/201101-6957/)

---

### Post by mörgæs on 2013-12-17
I can't promise that it will fix the overheating, it's just an easy first test to do.

Always fresh install, not an in-place upgrade.

---

