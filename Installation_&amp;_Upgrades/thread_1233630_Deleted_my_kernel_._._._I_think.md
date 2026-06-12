---
title: "Deleted my kernel . . . I think?"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by zmzach on 2009-08-06
Well the long and the short of it is I think I accidently deleted my kernel. This folder got deleted: /lib/modules/2.6.24-24-generic

However with apt-get update I was able to at least get the computer going again by booting to the 2.6.23-23 kernel in grub.

Now though, I can't use wireless, don't have sound, and I'm missing my "JUNK" folder on my desktop with all my music and stuff in it.

Should I just deal with these problems individually, or is there an easier way to fix them all at once?

Thanks

---

### Post by lykwydchykyn on 2009-08-06
Well, I don't know about your JUNK folder, but for the rest, try this:
```

aptitude purge linux-image-2.6.24-24-generic
aptitude install linux-image-2.6.24-24-generic linux-restricted-modules-2.6.24-24-generic


```

Then reboot and see where that leaves you.

Oh and, whatever you did to delete that folder, don't do it again. :-D

---

### Post by zmzach on 2009-08-07
> 

Then reboot and see where that leaves you.

Oh and, whatever you did to delete that folder, don't do it again. :-D

I did reboot, and these are the problems that I am having

---

### Post by renkinjutsu on 2009-08-07
you didn't delete your kernel, you just deleted the modules.. 
uninstalling and reinstalling the kernel using apt-get should fix it...

also.. why did you reboot it would've been easier to fix when your system were still running

---

### Post by lykwydchykyn on 2009-08-07
> **zmzach said:**
> I did reboot, and these are the problems that I am having

Please re-read the post; I mentioned two commands to run before you reboot again.  Those would be the critical part of the process.

---

