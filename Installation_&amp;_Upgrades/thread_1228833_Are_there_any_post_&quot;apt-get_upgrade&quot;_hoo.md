---
title: "Are there any post &quot;apt-get upgrade&quot; hooks or signals?"
date: 2009-08-01
forum: Installation &amp; Upgrades
---

### Post by ryankask on 2009-08-01
Hello all. I just installed a blazing fast Xubuntu on a fresh new disk. I boot to this OS from another disk using GRUB that is managed by a Kubuntu installation on that other disk.

Whenever Xubuntu (for that is what I am running but it shouldn't matter) gets a Linux kernel update, I have to manually mount the other disk and change the boot settings to use the new kernel in [otherdisk]/[kubuntu]/boot/grub/menu.lst.

I want to write as script so I can stop doing this repetitive task.

Are there any signals, anything at all to hook into either in the apt-get system or perhaps when Linux boots up (i.e. does it notice it's using a different/upgraded kernel)? 

Any help is much appreciated.

cheers,
Ryan Kaskel

---

### Post by running_rabbit07 on 2009-08-10
Go into Synaptic Package Manager and install startupmanager and you will be able to tell it to boot the newest kernel.

---

