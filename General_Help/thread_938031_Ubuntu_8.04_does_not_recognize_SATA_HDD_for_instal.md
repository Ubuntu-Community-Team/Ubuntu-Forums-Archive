---
title: "Ubuntu 8.04 does not recognize SATA HDD for installation / boot"
date: 2008-10-04
forum: General Help
---

### Post by shmoe010 on 2008-10-04
I have been running Hardy for a while now, but I built a new computer and got a new hard drive with it (750gb sata II) and for some reason Ubuntu doesn't see it. My old HDD was SATA as well and worked right out of the box. I know that HDD is okay because I have vista (shiver) installed, and unfortunately that's what I'm using to write this post! :)

I followed some threads on the forums and managed to get Ubuntu installed by adding the boot option "all_generic_ide". Another suggestion was to set my BIOS to 'raid' mode but that didn't work. However, pretending my SATA drives are IDE does work.

The problem I'm having now is that after installing it successfully, I can't get back into it! GRUB won't even come up after setting my linux drive as primary in the BIOS. So my question is: a)how can I add the all_generic_ide boot option without getting into ubuntu; and b)is there an easier or more permanent way to fix this? 

Thanks! :)

---

### Post by shmoe010 on 2008-10-04
bump

---

### Post by cariboo on 2008-10-04
You may want to look at your bios to see if there is a setting for emulation mode, it should be something like AHCI mode. You should have to set anything else but boot order. I would suggest booting from the liveCD. Have a look here for instructions:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

One other thing, forum policy is to only bump after 24 hours.

Jim

---

### Post by shmoe010 on 2008-10-04
> **cariboo907 said:**
> You may want to look at your bios to see if there is a setting for emulation mode, it should be something like AHCI mode. You should have to set anything else but boot order. I would suggest booting from the liveCD. Have a look here for instructions:

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

One other thing, forum policy is to only bump after 24 hours.

Jim

Oops, sorry. It got dropped to like the third page and I got ancy. Vista hurts me. :/

---

### Post by shmoe010 on 2008-10-07
Bump... 2 days still can't boot into hardy

---

