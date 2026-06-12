---
title: "Vista won't boot post-Ubuntu install"
date: 2009-09-11
forum: Installation &amp; Upgrades
---

### Post by Whisp3r on 2009-09-11
I got this new laptop with Vista (ick). Anyways, I went ahead and installed Ubuntu, using the Ubuntu partitioner. Anyways, it installed fine, I set up Ubuntu the way I liked it, rebooted to Vista, set it up the way I like it, and then... wham. Can't reboot to Vista. When I get to the GRUB screen, I select Vista, it loads for about half a second, and then I get a blue screen of death. Unfortunately, the blue screen lasts about .5 seconds so I can't read it.

When I do a system repair on Vista with the driver CD, I get the following error:

Unspecified changes to system configuration might have caused the problem.
Repair action: System files integrity check and repair
Result: Failed. Error code=0x4005.

How do I fix Vista to get it to boot up again? :(

---

### Post by creiss on 2009-09-11
Sounds like a corrupted Windows partition to me, or at least a damaged file system. Try gparted, it has some minor repair capabilities (google). Good luck.

But besides that, nothing short or a reinstallation will help. :/

-Chris.

---

### Post by Yvan300 on 2009-09-11
+1, blue screens of death are a sign that it is time to reinstall. But hey you should be able to copy over all your media by mounting the window's partition in ubuntu.

---

### Post by ronparent on 2009-09-11
Just a quick note. Others have also had bad outcomes trying to use gpated to repartition a vista partition. It has been generally recommended that vista be repatitioned only from within vista using the built in or a compatible partitioner (NOT Partition Magic).

---

### Post by Whisp3r on 2009-09-11
Thanks all. I'll reinstall everything and let you know how it turns out.

---

