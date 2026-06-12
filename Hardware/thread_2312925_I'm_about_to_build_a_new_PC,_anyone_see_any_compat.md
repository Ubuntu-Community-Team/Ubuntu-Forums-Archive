---
title: "I'm about to build a new PC, anyone see any compatibility issues with this build?"
date: 2016-02-08
forum: Hardware
---

### Post by kurmudgeon79 on 2016-02-08
I put together a Skylake build with Nvidia 960 GPU.  Here's a link to the build: [http://pcpartpicker.com/p/4LkxXL](http://pcpartpicker.com/p/4LkxXL)

I know that the GPU isn't current, but I can upgrade that later on.  I will be using this primarily for video and audio editing and as a media server.  It will be my main desktop machine at home.  I think this build will be perfect for Ubuntu 15.10+, but wanted to know if the community has had any issues with any of this hardware before purchasing.

I'm looking for a build that is somewhat future proof (for the next 5 years at least), is powerful, and compatible with Ubuntu.  Things I'm unsure of with compatibility are the following:


[LIST=1]
[*]Intel Skylake support
[*]Support for this NVidia 960 GPU
[*]USB 3.1 (USB C) support
[*]Support for M.2 SSD drives as the main OS drive
[*]Support for the Intel GbE LAN chip onboard the motherboard
[*]Support for this motherboard in general
[/LIST]

Any input is appreciated.

---

### Post by weatherman2 on 2016-02-08
If you might upgrade the video card later, save the money on that Gigabyte/NVidia graphics card, because you might not need it anyway, unless you are planning to play games on it.  Integrated video on a modern CPU is quite good. That motherboard has DVI and HDMI so if your monitors can use those, start there and see if you even need a separate video card.

I suspect you will have some compatibility issues on the newer hardware with Ubuntu for a few releases.  You might have to build a custom kernel or something, so be prepared to do that.

---

### Post by oldfred on 2016-02-08
Bucky Ball says Gigabyte H170 works.
[http://ubuntuforums.org/showthread.php?t=2312650](http://ubuntuforums.org/showthread.php?t=2312650)

Another thread on same issue, but no response from OP on if it worked.
[http://ubuntuforums.org/showthread.php?t=2306715](http://ubuntuforums.org/showthread.php?t=2306715)

You probably need the newest kernel & support software. And nVidia proprietary drivers. Best installed from ppa, not nVidia.

---

### Post by kurmudgeon79 on 2016-02-08
Do you know much about installing Ubuntu on an M.2 SSD drive and whether or not this would be supported?

Edit: I just went through [your second link]("http://ubuntuforums.org/showthread.php?t=2306715") and saw that 15.10+ should work after updating ALSA with the Z170 board.  I guess I'll give it a shot.  My current machine is 8 years old and still running 12.04.  I like using Chrome, but Google is dropping support next month; it's time to upgrade my machine any way.  I'm still wondering about installing Ubuntu to the M.2 SSD though.

Thanks for the help!

---

### Post by weatherman2 on 2016-02-08
I'm not sure why you'd have issues with an M.2 SSD - it should appear to an OS as just another drive, I'd guess.

Google is dropping support for Chrome in 12.04 AND for 32-bit Linux.  If your old machine has a 64-bit CPU and is using the 64-bit Ubuntu 12.04, you could upgrade it to 14.04 to keep using Chrome.  Most 8 year old CPUs should be 64-bit capable.   (One exception would be Intel's Core Duo line which is only 32-bit, but that came out in 2006; Core 2 Duo should be all 64-bit.  Some Pentium 4 CPUs are 64-bit as well.)

---

### Post by kurmudgeon79 on 2016-02-08
Yeah, my current machine is a [Core i7-920]("http://ark.intel.com/products/37147/Intel-Core-i7-920-Processor-8M-Cache-2_66-GHz-4_80-GTs-Intel-QPI") from 2008.  The machine works perfectly fine, but my GPU has some minor issues.  The problem for me is I highly customized my Ubuntu 12.04 install, so there's no simple upgrade for me other than wiping and starting over.  Since I have to wipe and start over, I was thinking it might be a good time to just completely start over with a new build.  I've never used M.2 before, can't wait for the chance.  I think I will wait until 16.04 is released, then order the parts.  I'll just deal with an out-of-date Chrome for a month or use Firefox for the meantime.

I modified my parts list slightly by bumping up to the [Core i7-6700]("http://ark.intel.com/products/88196/Intel-Core-i7-6700-Processor-8M-Cache-up-to-4_00-GHz") that has hyperthreading.  I got accustomed to having hyperthreading on my current machine and depend on it now.  I took your advice and ditched the GPU for now and will take another look at that as an upgrade at a later date.  Here's the new parts list, basically the same price as before: [http://pcpartpicker.com/p/38sRQ7](http://pcpartpicker.com/p/38sRQ7)

Thanks for the help!

---

### Post by weatherman2 on 2016-02-08
There was a big performance jump from 1st generation Core (your old i7) to 2nd generation (Sandy Bridge), mostly regarding integrated video performance, which has been much improved ever since.  I think even going to a Sandy Bridge i7 would give you a nice boost.

Hyperthreading isn't magical.  It just gives each core more performance in some cases, but it depends on the OS's ability to schedule things in parallel.  If you are doing one task, hyperthreading does nada for you.  If you are doing four tasks on a quad core CPU, hyperthreading does almost nothing for you.  If you have a bunch of parallel tasks going at the same time, say on a multi-user server, hyperthreading could give you a big boost but probably not on a single user Linux machine unless you are using software designed to parallel-ize the tasks it is performing.  Hyperthreading helps more in Windows I believe because it is always running your anti-virus in the background, for example, something you generally don't need to worry about with Ubuntu.

If you look at the performance benchmarks on your old i7 vs. the new one you are proposing, the performance is about 2X, even single thread (one task) performance, and that doesn't even account for the better video performance you should expect.  But power consumption is about 1/2 - amazing!

Sometimes I laugh at you guys who build these fancy, high-performance beasts.  I usually go for the cheapest thing I can get away with.  My fastest CPU (of several computers, all Ubuntu) is an Ivy Bridge i3, which to me still seems good for a few more years.  My media servers are slow Celerons, but they work great for streaming videos on my big TVs.

You might try upgrading that old i7 machine anyway.  You've only got another year of support for it, anyway - you'll need to do something.  It might be easier than you imagine.

---

### Post by oldfred on 2016-02-08
To partition M.2 device you may need newer gparted.
M.2 will be a NVMe device and is new, so support just starting to work.
Some parted were updated in 2014 and some very recently, so again you may need new kernel, support software and drivers.

 gparted should be at least version 0.24.0-1 to recognize NVMe devices
[URL="http://gparted.sourceforge.net/index.php"]http://gparted.sourceforge.net/index.php

[/URL]
 Support for NVMe in grub-mkdevicemap fixed in 2014
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1275162)
spec entry for nvme devices (UEFI v2.4A 9.3.5.22)

[URL="http://gparted.sourceforge.net/index.php"]
[/URL]

---

### Post by kurmudgeon79 on 2016-02-08
Awesome.  Thank you for the info, I appreciate it!

---

