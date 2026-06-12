---
title: "Toshiba Satellite M40 freezes with Hoary 5.04"
date: 2005-09-05
forum: Hardware &amp; Laptops
---

### Post by frailis on 2005-09-05
Hello everybody,

I've correctly installed kubuntu hoary 5.04 into a Toshiba Satellite M40-193. A similar model in the USA is Toshiba Satellite M45. 

I solved the hotplug problem thanks to the previous posts in this mailing list. However during the normal usage of the system. I'm experiencing random freezes (mouse pointer stops moving and keyboard events are not handled).

Maybe the problem is the ACPI, not yet perfectly supported for this new system, or the SATA controller.

Did someone have the same problem and find a solution?

Thank you in advance for any help.

Marco

---

### Post by Titan3025 on 2005-09-10
I am having the same problem with a Thinkpad T43p :-( Even with Breezy PR1.

I guess it is a SATA problem. I hope they will fix it soon with a Kernel Update.

---

### Post by frailis on 2005-09-13
Hi,

I've solved the problem recompiling the kernel and of course using another configuration (.config). I took the configuration file from the knoppix 4.0 distribution.

---

### Post by hshen on 2005-09-20
[QUOTE=frailis]Hi,

I've solved the problem recompiling the kernel and of course using another configuration (.config). I took the configuration file from the knoppix 4.0 distribution.[/QUOTE]

First, what did you exactly do to solve your "hotplug" hang problem? I tried the tricks such as adding  "irqpoll" and "noapic" to grub or adding modules/devices to hotplug blacklist mentioned in other threads related to M40 hotplug hang, but nothing works. My own way to solve this "hotplug" hang problem is to comment out pci.agent in /etc/hotplug/pci.rc. I believe that something wrong during the executation of pci.agent but cannot identify exactly where. 

After that, I can run Hoary reasonably ok (after another battle to make wireless connection work), but I have the same problem  as you that system freezes occasionally. Now the problem becomes more serious when I tried to tar whole root file system as a backup. tar executation never ends normally. tar freezes at random places after about 200 - 300M tar file is written to the disk. I have never built a kernel my own. Where do you get the knoppix configuration and how to use it when you build the kernel?

Thanks
hshen

---

### Post by frailis on 2005-10-08
Hi, 

I've seen your post only now.
To solve the hotplug hang problem, as specified in some previous post, I added the following line to the "/etc/hotplug/blacklist" file:

ohci1394

because this driver seems to cause that hang problem. With the new kubuntu breezy candidate release this is not necessary.

The system freezes were systematic and the problem is in some kernel option. This problem was present also in the kubuntu breezy preview.It's not difficult to compile the kernel but  if you want I can send you a debian package with my kernel image. After installing it, you will simply have another entry in the grub menù.

If you want to learn the kernel compilation on a debian system, I used the following tutorial:

[http://newbiedoc.sourceforge.net/system/kernel-pkg.html](http://newbiedoc.sourceforge.net/system/kernel-pkg.html)

Differently from this tutorial, in an ubuntu/kubuntu system the kernel source package is named "linux-source". Once the debian package is created, you can install it with dpkg -i <kernel-image>.deb and it will automatically update your grub menu. Instead of configuring the kernel on your own you can recover a configuration file from a live distribution: just copy the file /boot/config-2.6.xxxx in the live distribution to your /usr/src/linux/ directory naming it ".config" and use the command "make oldconfig" in that directory (I used the knoppix 4 live distribution).
Best regards,

Marco

---

