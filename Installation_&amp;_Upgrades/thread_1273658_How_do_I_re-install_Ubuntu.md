---
title: "How do I re-install Ubuntu?"
date: 2009-09-23
forum: Installation &amp; Upgrades
---

### Post by zking on 2009-09-23
My computer is dual-booted with Windows Vista and Linux Ubuntu. 

I need to re-install Ubuntu, because I incorrectly installed it and ended up with only 2.5 GB partition ([http://ubuntuforums.org/showthread.php?p=7658271#post7658271](http://ubuntuforums.org/showthread.php?p=7658271#post7658271))

Now, I would simply uninstall Ubuntu, and then install it again, but the problem is that I don't have a Windows Installation CD (this is needed to uninstall Ubuntu from a partition). 

I don't know. Maybe I don't need this CD? I'm confused. 

Please help! :confused:

---

### Post by shaunsmith_99 on 2009-09-23
Yeah, I'dd like to see something on this too... 

 Isn't there some method to expand the size of the ~ext3 partition and resize the swap files without a clean install?!?! It's only logical... :confused:

---

### Post by SuperSonic4 on 2009-09-23
> **zking said:**
> I don't have a Windows Installation CD (this is needed to uninstall Ubuntu from a partition).

No. That's lies, you can use any Live CD or even the GParted Live CD.

Reinstalling is the same as installing in Linux, just give it more memory when you're at the appropriate stage.

(Or create manual partitions - better IMO because you're in control from start to end)

---

### Post by SuperSonic4 on 2009-09-23
> **zking said:**
> My computer is dual-booted with Windows Vista and Linux Ubuntu. 

I need to re-install Ubuntu, because I incorrectly installed it and ended up with only 2.5 GB partition ([http://ubuntuforums.org/showthread.php?p=7658271#post7658271](http://ubuntuforums.org/showthread.php?p=7658271#post7658271))

Now, I would simply uninstall Ubuntu, and then install it again, but the problem is that I don't have a Windows Installation CD (this is needed to uninstall Ubuntu from a partition). 

I don't know. Maybe I don't need this CD? I'm confused. 

Please help! :confused:

> **shaunsmith_99 said:**
> Yeah, I'dd like to see something on this too... 

 Isn't there some method to expand the size of the ~ext3 partition and resize the swap files without a clean install?!?! It's only logical... :confused:

You can do that with a live CD too although if you move the swap partition you'll need to manually edit fstab which isn't too hard

---

