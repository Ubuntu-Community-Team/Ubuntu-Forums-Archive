---
title: "Installing ubunto on older hardware"
date: 2009-04-15
forum: Installation &amp; Upgrades
---

### Post by pinkturbokitty on 2009-04-15
I want to install Ubunto on a beige box pentium 3 1ghz. And I was wondering if Pentium 3 is too slow for it/incompatible. How can I find a resource to tell me whether not there are drivers for my hardware such as video, sound board and NIC?

Any advice or direction will be greatly appreciated. 

And I appoligise if this is a stupid question or this question has already been posted on this forum (I searched and found nothing).

---

### Post by gfe on 2009-04-15
First, if you haven't done so already, try running a Live CD. If it runs the hardware, then you know it'll work.

Second, if you don't have much memory, you might try Xubuntu instead. It's a bit more friendly with low-end machines.

---

### Post by rucadulu on 2009-04-15
I had Ubuntu 8.04 running on two old P3's I gave a friend of mine. One was 500mghz with 384mb of ram and the other was 700mghz with 512mb of ram. I have tried it with 256mb of ram on the 500ghz unit but it does not function as well. I would say to try to stay at or above 384mb of ram. Your 1 ghz P3 should handle it no problem with 384mb or more of ram. I also would not use a Ubuntu addition newer than 8.04 as the proprietary driver support for graphics card with older chip sets like nvidia geforce2 and has been removed.

---

### Post by abn91c on 2009-04-15
i had ubuntu 8.10 on a 400mhz celeron with 512mb ram, it ran Ok,low graphics mode but only because it had a SIS video car. That same PC now has Mandriva 2009(KDE) and I donated it to the daycare my wife works at, and it is very usable

---

### Post by Jimmynemo2 on 2009-04-15
Anyone know if there is a hardware list by Ubuntu version numbers? Minimum requirements page, etc?

Thanks

---

### Post by gfe on 2009-04-16
Come to think of it, a computer I was running until about three months ago and only slightly better than the 1GHz P3 of the OP ran fine with Ubuntu 8.04, but ran a bit better with Xubuntu. (But then the motherboard fried when my power supply went out, and now it doesn't run anything>)

Recently, I loaded Xubuntu onto a 10-year-old 475 MHz laptop with only 192K RAM. Xubuntu handled all of the hardware just fine, but it ran slowly, seeming like it was using the swapfile way, way too much. The hard drive was always going, and programs would take long to load.

So I tried installing Puppy Linux on the machine. It ran like a charm.

I'm not sure how helpful a hardware compatibility list is going to be -- there very well may be some hardware that isn't officially supported but uses the same chipset or drivers or whatever as something that is.  And that's one of the advantages of most distros these days: You can try them out without installing them.

---

