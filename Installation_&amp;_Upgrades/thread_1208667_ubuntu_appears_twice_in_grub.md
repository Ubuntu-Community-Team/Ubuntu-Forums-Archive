---
title: "ubuntu appears twice in grub"
date: 2009-07-09
forum: Installation &amp; Upgrades
---

### Post by snu on 2009-07-09
title says it all, actually
it looks like this
> 
Ubuntu 9.04, Kernel 2.6.28-13-generic
Ubuntu 9.04, Kernel 2.6.28-13-generic (recovery mode)
Ubuntu 9.04, Kernel 2.6.27-7-generic
Ubuntu 9.04, Kernel 2.6.27-7-generic (recovery mode)
other operating systems
Windows Vista/Longhorn (loader)


i suspect it might have something to with me installing Ubuntu 8.10, then updating to 9.04, and then, due to reinstalling, repeating that procedure.

this guide [http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/) suggests simply deleting one kernel from the lists, but i wonder if old files from the older kernel might not lead to problems?
also: is the ...27-7-gen..-kernel the older one? or does the smaller number (27 <28 ) not necessarily mean that it's older?

in case you ask me to give further information about my system, please also post me the commands i must use to get them. i am yet not very familiar with ubuntu.
(in the following thread the asking person is asked to do so. it's just i don't know if the same informations are of relevance in my case, [http://ubuntuforums.org/archive/index.php/t-1030581.html](http://ubuntuforums.org/archive/index.php/t-1030581.html) )


thanks in advance

---

### Post by raymondh on 2009-07-09
> **snu said:**
> title says it all, actually
it looks like this


i suspect it might have something to with me installing Ubuntu 8.10, then updating to 9.04, and then, due to reinstalling, repeating that procedure.

this guide [http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/](http://www.howtogeek.com/howto/ubuntu/clean-up-ubuntu-grub-boot-menu-after-upgrades/) suggests simply deleting one kernel from the lists, but i wonder if old files from the older kernel might not lead to problems?
also: is the ...27-7-gen..-kernel the older one? or does the smaller number (27 <28 ) not necessarily mean that it's older?

in case you ask me to give further information about my system, please also post me the commands i must use to get them. i am yet not very familiar with ubuntu.
(in the following thread the asking person is asked to do so. it's just i don't know if the same informations are of relevance in my case, [http://ubuntuforums.org/archive/index.php/t-1030581.html](http://ubuntuforums.org/archive/index.php/t-1030581.html) )


thanks in advance

You just upgraded the kernel.  it's OK to have 2 kernels ... just in case one breaks, you can always use the other while working on the borked one.

The newer kernel is the higher end-number.

If you want to set boot defaults, etc,  download startupmanager and set default and other preferences there.  In this case, if you want, set the default to 28-13 generic.

---

### Post by snu on 2009-07-09
okay.
thank you

---

### Post by raymondh on 2009-07-09
> **snu said:**
> okay.
thank you

you're welcome ... happy ubuntu-ing.

---

