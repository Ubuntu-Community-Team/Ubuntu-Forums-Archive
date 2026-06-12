---
title: "removing available kernels"
date: 2009-08-25
forum: Hardware
---

### Post by mmmmna on 2009-08-25
UNR 9.04, Asus EeePC 900A which was built with 4G SSD.

My 'Administration' tab offers 'Startup Manager', I see I can choose to startup with any of 4 kernels. I only have a few hundred megs of empty disk space and opportunities to free more space are welcomed.

I'm fairly new to Ubuntu, sooooooo....

How should I go about removing the unwanted kernels, how do I go about preventing more than 2 kernels fallback?

---

### Post by tgeer43 on 2009-08-26
I've never run the netbook remix but hopefully the same instructions will apply as for regular Ubuntu.

Just do a quick Google for: ubuntu remove old kernels
and you'll find lots of good instructions for doing this.

I'd copy them here for you but it's getting late.

tgeer

---

### Post by x33a on 2009-08-26
first of all the 4 entries you are seeing are actually 2 kernels. 2 entries are for the safe mode.

so, if you are sure that everything is working great with the current kernel, you can remove the previous one.

take a look here:

[http://ubuntuforums.org/showthread.php?t=1054269](http://ubuntuforums.org/showthread.php?t=1054269)

---

### Post by drs305 on 2009-08-26
If you clcik to the "SUM" link in my signature line it will take you to a post on StartUp-Manager. SUM will "hide" kernels but not remove them, but removing them is also discussed in the link.

To remove kernels, use Synaptic and find the "linux-image" entries. A typical entry would be "linux-image-2.6.28-15-generic". You can also remove the equivalent "linux-headers-2.6.28-15-generic". If you remove them from the system with Synaptic they will also automatically be removed from the menu.lst.

Make sure you don't remove your running kernel (although the system should not let you). You can find it by running "uname -r" in a terminal. It's generally a good idea to keep at least two kernels - the latest and an older one you know works.

---

### Post by mmmmna on 2009-09-24
thanks, drs305 and x33a. I uninstalled 3 unused kernels viasynaptic.

---

