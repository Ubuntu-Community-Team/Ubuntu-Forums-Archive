---
title: "Why linux kernel updates make many things incompatibel?"
date: 2008-08-10
forum: General Help
---

### Post by yesint on 2008-08-10
Dear All,
(This post is a kind of "just curious" question, no intention to start "holy wars")

I'm a long-time linux user, but I was never interested in the kernel design and other under-the-hood issues. However, after next kernel update I've found that VirtualBox doesn't install at all   and some other things does not work any more... I started to think why no such things happen in Window$. Indeed, there is no such thing as incompatibility with the kernel in Window$. If something is compiled, than it works for years despite any updates and patches (well, sometimes there are problems, but they are mostly just bugs). In Linux one need to keep many programs synchronised with the kernel, especially virtualization apps. 
Is there any philosophy behind or this is just unfortunate design of the kernel in this respect?
The kernel itself is updated very often. I understand that the bugs are constantly fixed and new features added, but why this makes other things broken? If support for some hardware XX is added to kernel, why VirtualBox refuses to work with this kernel any more? What is the relation between the things after all?

---

### Post by jimv on 2008-08-10
In Windows the equivalent of a kernel update is a service pack, and they tend to break all kinds of things.

In the case of VirtualBox OSE, it uses kernel specific modules.  I got tired of this breaking all the time and now use the non-OSE version of VirtualBox, which doesn't require the kernel specific modules.  (Thus won't break during kernel updates.)  It also support USB devices and virtual SATA drives, which the OSE version does not.

You can download the non-OSE version here:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

---

### Post by linux_tech on 2008-08-10
QA, software testing, rapidly changing technology and frequent release dates.

When kernal changes are made all kernal modules must be compatible also.
Since some of the modules are devices drivers if the kernal is changed there may be some modules that do not load correctly or work correctly resulting in a device that may not function correctly. Modularity is good, modules can changed or added.

---

### Post by yesint on 2008-08-11
> **jimv said:**
> 
You can download the non-OSE version here:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)

That's what I just decided to do as well!

---

### Post by yesint on 2008-08-11
> **linux_tech said:**
> 
Since some of the modules are devices drivers if the kernal is changed there may be some modules that do not load correctly or work correctly resulting in a device that may not function correctly. 

Well, the question is actually why the device drivers (and virtualization modules) are so much coupled to all other things in the kernel? I'm not an expert at all, but it seems strange for me that the piece of code, which does low-level work with the hardware needs changes every time even though the device is still the same. IMHO, modularity should avoid such things, but it does not as far as I can see. 
Again, if I want to use the driver designed for antique Win2000 in Vista it often works! (Don't worry, I don't use Vista :) )
Is this the same for, say, BSD/Mac?

---

### Post by adult swim on 2008-08-11
yesint, if your only problem is virtualbox after a kernel upgrade, it should be an easy fix.  whenever i run virtualbox PUEL after a kernel upgrade it tells me something along the lines of the module isnt in the kernel and to run /etc/init.d/vboxdrv setup to fix it.  i run ```
sudo /etc/init.d/vboxdrv setup
``` from a terminal select it from the applications menu and it starts up.

---

### Post by mcduck on 2008-08-11
> **yesint said:**
> Well, the question is actually why the device drivers (and virtualization modules) are so much coupled to all other things in the kernel? I'm not an expert at all, but it seems strange for me that the piece of code, which does low-level work with the hardware needs changes every time even though the device is still the same. IMHO, modularity should avoid such things, but it does not as far as I can see. 
Again, if I want to use the driver designed for antique Win2000 in Vista it often works! (Don't worry, I don't use Vista :) )
Is this the same for, say, BSD/Mac?
The kernel modules are actually part of the kernel itself.

Drivers can be compiled either into the kernel itself, or as modules which can be loaded and unloaded when necessary, but they are still parts of the kernel.

This is only a problem with proprietary drivers and other stuff like that, ie. modules developed by other people than the kernel developers, and that often don't have source code available.

Windows avoids the probem simply by not really updating the kernel much at all.. The NT kernel used by NT/2000/XP/Vista is already ridiculously outdated. :D Also Windows runs drivers in kernel level, probably because most of the Windows drivers are written by 3rd party companies.

---

### Post by yesint on 2008-08-13
> **mcduck said:**
> The NT kernel used by NT/2000/XP/Vista is already ridiculously outdated. :D 

I guess that Windows users have no idea about this :) There is a good side - everything is compatible.

---

### Post by Mgiacchetti on 2008-08-13
> **jimv said:**
> In Windows the equivalent of a kernel update is a service pack, and they tend to break all kinds of things.

In the case of VirtualBox OSE, it uses kernel specific modules.  I got tired of this breaking all the time and now use the non-OSE version of VirtualBox, which doesn't require the kernel specific modules.  (Thus won't break during kernel updates.)  It also support USB devices and virtual SATA drives, which the OSE version does not.

You can download the non-OSE version here:

[https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI](https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.6-G-F@CDS-CDS_SMI)


actually the non ose version does break during kernel upgrades, I need to go to synaptic, highlight virtualbox and click package > configure  to recompile the kernel modules.

---

