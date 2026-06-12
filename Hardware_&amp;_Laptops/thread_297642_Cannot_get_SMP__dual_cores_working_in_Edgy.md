---
title: "Cannot get SMP / dual cores working in Edgy"
date: 2006-11-11
forum: Hardware &amp; Laptops
---

### Post by stevenmansour on 2006-11-11
Hello,

I just took the plunge - I left Mac OS X for Ubuntu. 

I've just finished installing Ubuntu on a Dell M90 core 2 duo. I've finally got everything set up properly (Beryl, Intel 3945 wireless, NVIDIA drivers, etc), but I can't for the life of me get Ubuntu to recognize both cores.

It says [here in the Ubuntu guide]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Multicore_Support") that it should be as easy as ```
sudo apt-get install linux-686-smp
```. I do that, with no errors, but then when I run ```
cat /proc/cpuinfo
```, I still only see a single processor.

Is there anything else I need to do to enable multicore? Do I need to recompile the kernel?

Thanks alot (my first post here :D )!

---

### Post by jedir0x on 2006-11-15
Did you try rebooting after installing?  Kernel changes (outside of kernel modules) required a reboot to take effect.  It's pretty much the only reason you'd ever have to reboot a Linux machine :)

---

### Post by guitarist549 on 2006-11-17
Sorry for bumping this thread, but I'm having this problem as well.

I've tried installing the 686 kernel but that doesn't seem to help, even after restarting... What could be the problem?

---

### Post by Poison0985 on 2006-11-18
The same is happening to me here.

---

### Post by stevenmansour on 2006-11-18
Hi everyone,

I got this to work - actually, it was working the whole time - when I installed the linux-generic packages, Ubuntu added a GRUB entry for the new kernel, but didn't remove the old one (and didn't even make it default). 

So I got 4 entries for Ubuntu in GRUB now at boot time - I just had to select one of the new ones (GENERIC instead of 386) and voila, both my processors showed up.

Try it yourselves, then edit your GRUB file to make the new generic / SMP kernel default.

Good luck,

s.

---

### Post by ciscosurfer on 2006-11-18
If you've got this working, try prepending or appending your Post title to SOLVED, that way other users can see that your issue has been addressed and is working.

Cheers!

---

### Post by temna on 2006-12-01
I have been beating my head against this issue..  What is the grub configuration file supposed to look like?

---

### Post by ciscosurfer on 2006-12-01
> **temna said:**
> I have been beating my head against this issue..  What is the grub configuration file supposed to look like?You need to be using the 'generic' kernel that comes with (or is updated) with Edgy.  The 'generic' kernel is labeled as such and allows for both of your cores to function properly.

---

### Post by temna on 2006-12-01
> You need to be using the 'generic' kernel that comes with (or is updated) with Edgy. The 'generic' kernel is labeled as such and allows for both of your cores to function properly.

Ok, let's try this again..  I installed the "generic" kernel, but for some reason I'm still not getting both cores to show up..  I have tried restarting and reinstalling the generic kernel..  I have tried everything I can think of..  Edgy refuses to give me both kernels after upgrading from 6.06.1..  And my Edgy CD will not install (and yes, the CD does check out fine)..  I'm guessing the dual core kernel issue MIGHT be a grub issue, so I would like to see an example of a working grub configuration file.

---

### Post by ciscosurfer on 2006-12-01
> **temna said:**
> Ok, let's try this again..  I installed the "generic" kernel, but for some reason I'm still not getting both cores to show up..  I have tried restarting and reinstalling the generic kernel..  I have tried everything I can think of..  Edgy refuses to give me both kernels after upgrading from 6.06.1..  And my Edgy CD will not install (and yes, the CD does check out fine)..  I'm guessing the dual core kernel issue MIGHT be a grub issue, so I would like to see an example of a working grub configuration file.I'm just doing a quick search for issues related to this and have come up with this: [http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html](http://www.debianadmin.com/ubuntu-edgy-upgrade-common-problems-with-solutions.html)

I will post more when I get back to my Ubuntu machine.

If would recommend doing a clean install and not upgrading.  You will encounter more issues upgrading than if you do a clean install.  The clean install will most certainly locate other drives and partitions when you go to install it --  you GRUB menu.lst file will be correct then.

---

### Post by temna on 2006-12-05
> If would recommend doing a clean install and not upgrading. You will encounter more issues upgrading than if you do a clean install. The clean install will most certainly locate other drives and partitions when you go to install it -- you GRUB menu.lst file will be correct then.

Would that I could..  But I can't, so your suggestion doesn't help.  Did you not read where I could not install Edgy off the CD?  So much for the helpful forums.  Just a bunch of know it alls who cannot answer a simple question.

---

### Post by tommcd on 2006-12-05
According to this:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Multicore_Support](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_enable_Multicore_Support)
you no longer need to do: "sudo apt-get install linux-686-smp" The k7 and 686 kernels have been made obsolete by the generic kernel, which should give you dual core support automatically. I would suggest a clean install as well. Best way to avoid problems with an upgrade. 
As for grub, back up your menu.lst file first, then edit the file so the generic kernels are first in the list. This will boot the generic kernel by default.
For everything you would ever want to know about grub:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ciscosurfer on 2006-12-05
> **temna said:**
> Would that I could..  But I can't, so your suggestion doesn't help.  Did you not read where I could not install Edgy off the CD?  So much for the helpful forums.  Just a bunch of know it alls who cannot answer a simple question.Try the Alternate CD.  And we are trying to be helpful.  There's no need for the sarcasm.

---

### Post by syawillim on 2007-03-20
I'm having a similar problem, changing the generic kernel to first on the list resolves the dual processor issue but when I do this I loose my wireless pci card.

Any guidance would be appreciated.

---

