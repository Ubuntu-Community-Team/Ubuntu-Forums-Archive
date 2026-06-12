---
title: "Intel T2390 CPU and Ubuntu"
date: 2008-11-24
forum: Hardware
---

### Post by mpcengineering on 2008-11-24
I am trying to install Ubuntu 8.10 kernel 2.6.27 onto a U50SI2 novatech laptop and understand that the Intel T2390 dual cpu in this machine has problems with the Ubuntu kernel and bails almost immediately. I cannot really find anything recent about this subject but the thinking a few months back seems to have been that on release of the the more recent 2.6.27 kernel with Ubuntu 8.10, these issues should have been resolved. This appears not to be the case however, and attempting an install results in failure within a few seconds of booting from the 8.10 CD. This is also the case with a slightly older systemrescuecd disk I have tried to boot off (also linux based, but unsure as the kernel off the top of my head). Booting from a USB stick to install ubuntu results in the same behaviour also....

Has anyone had any experience with this setup and getting ubuntu to work on this CPU?

Thanks

Jon

---

### Post by mpcengineering on 2008-11-24
I have managed to find a workaround to this issue via another forum.  When booting off the CD you need to add a couple of arguments. Press F6 and add noapic and nolapic to the path given.  You should now be able to install Ubuntu, however you will lack power saving options for the laptop.  No great loss when windows is the alternative  :)

Might want to look at this as reference:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Cheers

Jon

---

