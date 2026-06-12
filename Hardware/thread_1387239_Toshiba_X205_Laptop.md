---
title: "Toshiba X205 Laptop"
date: 2010-01-21
forum: Hardware
---

### Post by davekiw on 2010-01-21
Ever since Karmic came out, my laptop hangs for almost 5 minutes during the boot process (live CD or installed versions).   I have had no problems with any older versions of Ubuntu.   This problem exists for any other distribution that uses Ubuntu as a base.   I've tried no acpi or apic, but no good.   :confused: Anybody have any ideas?   Maybe something has changed between 9.04 and 9.10 to cause this.   The laptop is an Intel core 2 Duo, 4GB RAM and an NVidia M8700 video card.

Thanks...

---

### Post by cenzorrll on 2010-01-21
try entering this in the terminal (from the [Grub2 Basics]("http://ubuntuforums.org/showthread.php?t=1195275") thread in the bugs section of the first post, although 5 minutes is a bit more than 10-30 seconds):

```
[CODE]sudo dpkg-reconfigure grub-pc
```

Select to load Grub 2 on the same device as the /boot partition. In your system BIOS, change the drive to boot from first to the drive with the /boot partition.[/CODE]

---

### Post by davekiw on 2010-01-21
A little hard to do with the live CD.   I've attached a file of where it hangs.

Thanks.

---

### Post by cenzorrll on 2010-01-21
hmm, can't be grub then.  i'm terrible at log files, but i'm sure somewhere in there you can find what it is that's causing the hang, unfortunately i don't know which one to look in for boot logs. they are kept in /var/log if you want to try your hand at it, make sure you take notice of what time you try to boot, and about where it hangs. It's most likely something that has a bad configuration in your startup. the log files should be able to tell you what is causing it, if you can find the right one.

sorry but i can't really help any more than that except for suggesting a reinstall (cowards way out, i know).

---

### Post by cenzorrll on 2010-01-21
just found this, i think it may be the same problem

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459837]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459837")

---

### Post by davekiw on 2010-01-22
This looks like my problem.   Thanks!   Maybe I'll wait for the new kernel (hopefully Ubuntu will include it in the next release), as I'm not knowledgeable enough to re-compile the kernel with a patch.

---

