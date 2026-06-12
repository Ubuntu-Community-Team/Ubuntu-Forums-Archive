---
title: "Kernel removal does not regain all the disk space used"
date: 2008-08-08
forum: General Help
---

### Post by sotirisp on 2008-08-08
Hi all,

I did a kernel compile/install to test some things. The whole process left my Filesystem with around 2.5GB less space.

I didn't had the expected results with that new kernel so i decided to remove it and stay with my older one.

Problem is that kernel removal didn't gave me back those 2.5GB space that it took to install it.

What else should i do to reclaim the occupied space except of the synaptic package complete removal?

Please be gentle, i am new on this one...

---

### Post by coffeecat on 2008-08-08
I've done a lot of kernel compiling in Gentoo (you have to :) ) but never in Ubuntu. The principle is the same, but some of the details are different so I can't tell you exactly what to look for.

I'm guessing that the packages you installed for preparing your own kernel will have set up a folder in /usr/src with source files and a load of other stuff. Then, when you compiled and installed your own kernel, a load more stuff will have been generated in /usr/src/whatever, a kernel image (and possibly an initrd image) will have been put in /boot, and lastly the modules for your home-brewed kernel will have been put in a folder in /lib/modules. So, when you uninstalled (I guess with the package manager - correct?) it would have deleted all the original stuff from /usr/src/whatever, but there will still be a lot of files in /usr/src/whatever as well as /lib/modules/whatever and the kernel image in /boot. Hence the lost space. There's probably also a .deb in /var/cache/apt/archives unless you selected 'remove completely' in Synaptic.

First - did you install a kernel package via Synaptic, or did you download one of the other kernel sources? Secondly, have a look in /usr/src and in /lib/modules and post back with the directories that are in there. If you're absolutely sure which is which, you can safely delete, but don't if you're not sure - you might delete the kernel headers and the loadable modules, which is not a good idea. :? Lastly, is there an unused kernel image (and associated files) in /boot?

---

### Post by sotirisp on 2008-08-08
Hi again and thanks for the fast reply,

i did a "make mrproper" from within the /usr/src/linux-source-blablabla.. directory (the one that contained the kernel source i wanted to get rid of) and, managed to recover about 3.2GB of space which is more than i expected to recover...

Question is: is it now safe to also delete that directory? Should i left it there?

Question 2: the kernel i just removed was the second kernel i tested today.
Seems that "make mrproper" removed this properly...

BUT before this kernel i had also installed today one more which i didn't remove with "make mrproper" command. I just used Synaptic full removal for that one, so i didn't recover another 2GB space from that one.
 That one's directory (/user/src/linux-source-blablabla...) was deleted by hand.

Is it possible now to do something and recover space taken from that kernel too?

I hope you understand what i mean...

---

### Post by coffeecat on 2008-08-09
Sorry about the delay getting back. It was night-time on this side of the world. :wink:

> **sotirisp said:**
> I hope you understand what i mean...

More or less. :) I should imagine that any folder with "source" in its name would be safe to delete. But before you do, in my installation of Ubuntu 8.04, I have 6 folders in /usr/src, namely: linux-headers-2.6.24-* and linux-headers-2.6.24-*-generic, where * = 16,17 and 19. So if you have any folders apart from these, they are almost certainly what you have installed from your kernel compiling adventure. (Irrelevent to your question, but it looks as though it's time I uninstalled the -16 stuff.)

Don't forget /lib/modules. I've got three folders: 2.6.24-*-generic. Again, * = 16,17 and 19.

---

