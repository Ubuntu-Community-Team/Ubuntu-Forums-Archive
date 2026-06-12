---
title: "Can't wake from suspend(to ram)"
date: 2008-11-27
forum: General Help
---

### Post by yellowman on 2008-11-27
I have a problem when I put my machine in suspend to ram(S3). It suspends fine, but when it's time to wake up, I see the powerbutton light up, the harddisk starts to spin for a while, but the screen remains blank, with the "no signal" sign. So it cleraly fails to resume.

I have tried to follow this guide: [https://wiki.ubuntu.com/DebuggingKernelSuspend](https://wiki.ubuntu.com/DebuggingKernelSuspend)

The part it says I should be looking for looks like this:> [ 22.932729] Magic number: 0:175:29
[ 22.932732] hash matches device ttydc

The complete dmesg looks like this: [http://pastebin.com/m3126fc60](http://pastebin.com/m3126fc60)

I don´t really understand what I´m supposed to get out of it.

I´m running Ubuntu 8.04, Nvidia 8500gt, Driver is 173.14.12. Motherboard is a Gigabyte GA-G33M-DS2 G33.

I have also tried booting up the 8.10 livecd and tried to suspend and resume from there, with the exact same result.

Any help is appreciated! Thanks!

---

### Post by yellowman on 2008-11-29
No ideas/suggestions? :confused:

---

### Post by 4Play on 2008-11-30
I have the exact same problem on a sony vaio SR130N:

 will suspend just fine, but when resuming, I get either a blank screen with a blinking cursor, or a completely black screen, or even a black screen with the caps lock and scroll lock leds flashing.

In all the situations I have to hard-reset the notebook, and then the logs file (/var/logs) dont report anything after the suspend and before the restart command :(

I am yet to to the suspend debugging you mentioned in your post, but from what I gather, the last thing on the dmesg (after the magic number) list is what is causing the problem, so you should add that module (ttydc, in your case) the the blacklist file (/etc/modprobe.d/blacklist add a line like this: blacklist ttydc) you should check what ttydc is first though :p

then try to suspend again.

I will report here if I get any enlightening results from the debugging on my laptop.

---

### Post by yellowman on 2008-11-30
Thanks for your answer!

I have tried adding "ttydc" to the "MODULES" part in /etc/default/acpi-support, I think that´s supposed to unload it before going in to suspend. And it dissapears from the dmesg "hash matches"-part, but it dosen´t change anything else.

But I have no idea what "ttydc" is, have searched but not found anything that makes sense.

I´ve never gotten a blinking cursor though, my screen never gets a signal on resume.

---

### Post by 4Play on 2008-12-01
You're right, adding the module to that file is much better then simply blacklisting it :p

I found that there are two files that relate to suspending modules:

For acpi-support, this is MODULES= in /etc/default/acpi-support. For pm-utils, it's SUSPEND_MODULES= in /usr/lib/pm-utils/defaults.

As to the debugging that I was going to perform, when I had everything set up, the resume worked!! out of the blue! but then, after a while it failed again (black screen) no idea why this is happening, will try again.

update: managed to run the test, but got no decent results:

> [    1.540918]   Magic number: 0:953:350
[    1.540920]   hash matches /build/buildd/linux-2.6.27/drivers/base/power/main.c:390

no more hash matches after that one :(

---

