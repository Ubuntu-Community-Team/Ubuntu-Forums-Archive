---
title: "snd-hda-intel: can't be loaded"
date: 2005-11-08
forum: Hardware &amp; Laptops
---

### Post by trixer on 2005-11-08
:???: Hi

My Computer is:
P4 LG775 2.66Ghz with 533Mhz of bus and 1Mb of Cache
Motherboard Intel 915GLVG [http://www.intel.com/products/motherboard/d915glvg/index.htm](http://www.intel.com/products/motherboard/d915glvg/index.htm)
Memory RAM: 1Gb DDR 400Mhz
Case: Sonata II of Antec Company
Hard Disk: Seagate Barracude 7200.7 of 120Gb
16x Super Multi DVD/CD Rewriter LG Company

Extra information:
Two Physical Partitions One of them of 91Gb for OS Windows XP Professional SP2
and the other one of 20Gb for Ubuntu 5.10

When my pc starts with Ubuntu 5.10

Ubuntu, kernel 2.6.12-9-386

My Ubuntu stop's in:

Starting hotplug subsystem..........for many many time and never continues!!

Then I restarts my pc again, and charge in mode:

Ubuntu, kernel 2.6.12-99386(recovery mode)

After being loaded appears this one:

[4294693.473000]        snd-hda-intel: can't be loaded
missing kernel or user mode driver snd-hda-intel
<6>pci_hotplug:PCI Hot Plug PCI Core version:0.5

I need that they help me please!!!

thanks:D

---

### Post by jezjones on 2006-01-18
I too am getting this problem. Although for me it is with the snd-intel8x0 module.

I am using a laptop with the ICH6 chip on it. I have gone through many efforts to get this to work, all to no avail.

I was using Hoary and although the sound did not work, it did boot. Now though i am getting this error message on boot and i cannot get further. This is since an upgrade to breezy. The same happens when going in single user mode.

I know that the sound is a mess and i wanted to do an install that skipped sound  completely so i just add the very latest alsa drivers, but it does nt seem to be able to deal with this missing driver.

There are many posts about this kind of thing but all without any answers, so instead of trying to fix this problem can anyone more experienced give me some tips on how to troubleshoot an install that wont boot. Sure once it boots there are a million things to look into, but being frozen is a really tough one to get out of.

Thanks

Jez 

p.s. to trixer, sorry to steal your thread, hopefully this will give it a bump.

---

### Post by jeremytaylor on 2006-01-18
did you come across this thread yet?
[http://www.ubuntuforums.org/showthread.php?t=111870&highlight=intel+hda](http://www.ubuntuforums.org/showthread.php?t=111870&highlight=intel+hda)

I haven't tried the new kernel, but using updated alsa things worked for me. You can either play with the etc/init.d/hotplug file as he suggests or in your /etc/hotplug/blacklist file add the following entries

intel hda audio
snd_hda_intel
snd_hda_codec

jeremy

---

### Post by jezjones on 2006-01-20
Thanks for the link i will look into that!!

Now as for the stuck boot and the hotplug black list, yes that is the solution but i was only able to do that by starting up a knoppix live session and mounting the hard disk, chroot to the hard disk and then editing the blacklist file.

Now i am back to the sound issue, so thanks for the link.

Jez

---

