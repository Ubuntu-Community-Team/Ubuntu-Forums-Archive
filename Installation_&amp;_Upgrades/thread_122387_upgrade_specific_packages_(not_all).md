---
title: "upgrade specific packages (not all)"
date: 2006-01-27
forum: Installation &amp; Upgrades
---

### Post by 5ketcher on 2006-01-27
Hi @ all,

I have Ubuntu running on my server (without a gui). I don't want to reboot the machine, but I want to be up to date :-)

Does anybody of you know the command to upgrade some specific packages? I know the command ```
 apt-get upgrade 
``` but I don't want to upgrade the kernel because of the reboot after that.

Cheers, Jan

---

### Post by aysiu on 2006-01-27
I believe there's a way in Synaptic Package Manager to freeze the version of a particular package. Unfortunately, that's Synaptic, which is graphical, and you probably don't even have X installed.

However, having had my kernel upgraded several times, I don't remember ever *needing* to be reboot afterwards or even being *asked* to reboot afterwards. What happens is that an extra kernel just gets added to the Grub boot menu. Just because you upgrade (actually, it just *adds* a kernel) the kernel doesn't mean you have to use the new kernel.

---

### Post by Klaidas on 2006-01-27
Hm, after I updated my kernel using Synaptic Package Manager, it asked me to reboot. The message was like "save all the unsaved work and reboot as soon as possible" :)

---

### Post by aysiu on 2006-01-27
[QUOTE=Klaidas]Hm, after I updated my kernel using Synaptic Package Manager, it asked me to reboot. The message was like "save all the unsaved work and reboot as soon as possible" :)[/QUOTE] Weird. I've never seen that. Has anyone else? Maybe it depends on how you installed it. I used apt-get for almost everything these days (instead of the update notifier, Add Applications, or Synaptic).

Certainly anyone running a server would use apt-get and not Synaptic, though.

---

### Post by stalefries on 2006-01-27
it is highly recommended to update after upgrading to a new kernel, because, i assume, it won't be used until one reboots. I don't know how to prevent the upgrade of a certain package, though.

---

