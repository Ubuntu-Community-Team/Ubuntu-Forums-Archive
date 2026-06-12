---
title: "Use PCI card over onboard Intel graphics"
date: 2009-11-01
forum: Hardware
---

### Post by urlacher3292 on 2009-11-01
I am trying to use my NVIDIA FX5200 over the onboard Intel graphics that my computer has. I am in karmic, and adding blacklist intel_agp & blacklist agpgart to /etc/modprobe.d/blacklist.conf doesn't work. I am looking for a way to blacklist the Intel card in Karmic.

---

### Post by urlacher3292 on 2009-11-01
Any ideas at all?

---

### Post by Yellow Pasque on 2009-11-01
> Any ideas at all?
Disable onboard video in the BIOS?

> adding blacklist intel_agp & blacklist agpgart to /etc/modprobe.d/blacklist.conf doesn't work
Did you run this after you did that?:
```
sudo update-initramfs -u
```

---

### Post by urlacher3292 on 2009-11-01
> **Temüjin said:**
> Disable onboard video in the BIOS?


Did you run this after you did that?:
```
sudo update-initramfs -u
```

The onboard card is disabled in the bios. The problem is that Ubuntu still detects it if it isn't blacklisted. I will try your second suggestion.

---

### Post by urlacher3292 on 2009-11-01
> **Temüjin said:**
> Did you run this after you did that?:
```
sudo update-initramfs -u
```

Thank you so much. This actually worked. Now I just need to switch from the nv drivers to the proprietary ones successfully.

---

### Post by Jules Delespy on 2009-12-03
I know this is an aged post, but I found it as I went through much trouble installing on an affected machine, and it is likely others will find their way here in the future.
The issue is installation on machines where 1) graphics processing is integrated into the motherboard and 2) a graphics card has been added as an upgrade. The cards are often Nvidia, but not necessarily. Often, the integrated graphics cannot be fully disabled in BIOS, or things go wrong even when the integrated graphics are disabled in BIOS.
This configuration can lead to a variety of problems, with the most severe being kernel panic at boot time, which results in the inability to either try out the liveCD, or install Ubuntu at all.
Since issues related to the combination of integrated graphics+graphics card show up in many forum categories, I collected a list of references where a solution was proposed. The first of those references comes from Alberto Milone (tseliot in Ubuntu forums), the author of EnvyNG, among other qualifications. You will notice that his HowTo validates the solution you describe here, and it seems reasonable to think that it is the best current solution.
The problem has existed in all versions of Ubuntu since at least version 5.10, and all the way to 27 November 2009 daily releases of 10.4. Strangely, it is possible that 8.04 was not affected. I have checked that the live CD of 8.04 indeed boots properly on affected machines, while none of the other versions do. As illustrated by the following links, other distros are affected as well. As a practical matter, this is very likely to stop many users from installing Linux on entry-level namebrand computers, which seems a shame.

here are the links:
[URL="http://www.albertomilone.com/nvidia_...integrated.txt"]
[/URL][http://www.albertomilone.com/nvidia_int ... grated.txt]("http://www.albertomilone.com/nvidia_intel_integrated.txt")
[http://ubuntuforums.org/showthread.php?t=1256691](http://ubuntuforums.org/showthread.php?t=1256691)
[http://ubuntuforums.org/showthread.php?t=1144043](http://ubuntuforums.org/showthread.php?t=1144043)
[http://ubuntuforums.org/showthread.php?t=675497](http://ubuntuforums.org/showthread.php?t=675497)
[http://ubuntuforums.org/showthread.php?t=1308919](http://ubuntuforums.org/showthread.php?t=1308919)
[https://bugs.launchpad.net/ubuntu/+sour ... +bug/55104]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/55104")
[http://www.bikechatforums.com/viewtopic.php?p=2356664](http://www.bikechatforums.com/viewtopic.php?p=2356664)
[http://www.nvnews.net/vbulletin/showthread.php?t=128934](http://www.nvnews.net/vbulletin/showthread.php?t=128934)
[http://ubuntuforums.org/showthread.php?t=196693](http://ubuntuforums.org/showthread.php?t=196693)
[http://ubuntuforums.org/showthread.php?t=635943](http://ubuntuforums.org/showthread.php?t=635943)
[http://ubuntuforums.org/showthread.php?t=192677](http://ubuntuforums.org/showthread.php?t=192677)
[http://ubuntuforums.org/showthread.php?t=496999](http://ubuntuforums.org/showthread.php?t=496999)
[http://ubuntuforums.org/showthread.php?t=1328043](http://ubuntuforums.org/showthread.php?t=1328043)
[http://ubuntuforums.org/showthread.php?t=1078576](http://ubuntuforums.org/showthread.php?t=1078576)
[http://ubuntuforums.org/showthread.php?t=295133](http://ubuntuforums.org/showthread.php?t=295133)
[http://javadocs.wordpress.com/2008/09/2 ... -gfx-card/]("http://javadocs.wordpress.com/2008/09/29/ubuntus-kernel-panic-freeze-with-an-asrock-motherboard-and-an-nvidia-gfx-card/")
[http://ubuntuforums.org/showthread.php?t=207303](http://ubuntuforums.org/showthread.php?t=207303)
[http://en.opensuse.org/NVidia_Suspend_HOWTO](http://en.opensuse.org/NVidia_Suspend_HOWTO)
[http://mepislovers.org/forums/showthread.php?t=6487](http://mepislovers.org/forums/showthread.php?t=6487)
[http://www.opensubscriber.com/message/s ... 46049.html]("http://www.opensubscriber.com/message/slug@slug.org.au/6446049.html")
[http://ubuntuforums.org/showthread.php?t=126492](http://ubuntuforums.org/showthread.php?t=126492)

---

### Post by ykasidit on 2009-12-13
Greetings,

I tried black-listing a computer as in some parts of the suggested [http://www.albertomilone.com/nvidia_intel_integrated.txt](http://www.albertomilone.com/nvidia_intel_integrated.txt) - it worked to use the offboard vga port on ubuntu 9.10 with nvidia geforce 5, but it worked only until I installed the nvidia driver, then after restart it would blink at some terminal login screen, like trying to start the gui but failed.

The same computer used to work with nvidia drivers in ubuntu 8.04 - using the deb installer (that didn't work on 9.10 for this issue, but link above worked) in [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/55104](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/55104), any suggestions for 9.10? This is probably an nvidia hardware driver issue?

---

### Post by urlacher3292 on 2009-12-13
> **ykasidit said:**
> Greetings,

I tried black-listing a computer as in some parts of the suggested [http://www.albertomilone.com/nvidia_intel_integrated.txt](http://www.albertomilone.com/nvidia_intel_integrated.txt) - it worked to use the offboard vga port on ubuntu 9.10 with nvidia geforce 5, but it worked only until I installed the nvidia driver, then after restart it would blink at some terminal login screen, like trying to start the gui but failed.

The same computer used to work with nvidia drivers in ubuntu 8.04 - using the deb installer (that didn't work on 9.10 for this issue, but link above worked) in [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/55104](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/55104), any suggestions for 9.10? This is probably an nvidia hardware driver issue?

Try booting into recovery mode and then select resume normal boot. This has worked for me especially with Kubuntu.

---

### Post by ykasidit on 2009-12-16
Thanks, urlacher3292. I'll try to try your suggestion when I get to that computer again.

---

