---
title: "problem with HP Pavilion dv6"
date: 2011-09-19
forum: Hardware
---

### Post by ilantal on 2011-09-19
I have a HP laptop where I am having a boot problem. I had it loaded up with software and all was working well. I wasn't sure what I had done but suddenly it would no longer boot correctly.
I have the disk divided into a "/" section for the ubuntu and a "/home" for user data. I formatted the "/" disk and reloaded ubuntu and my /home stayed in tact. Then I finally discovered where the problem was. When I closed the laptop lid, it went into suspend mode and the suspend mode killed something.
It would no longer boot properly (and still doesn't).
If I held off the power button and then turned it back on, it will go into the grub loader and ask me what to choose. If I choose either Ubuntu or Ubuntu recovery, it will never reach a useful stage.
However, if I choose to use a previous kernel I can get it to boot properly. That is until I turn it off and try to boot again. Then it will attempt to use the current kernel, which is apparently no good. (What went "bad" with it is probably connected to the suspend mode.)
My question is how do I "clean up" and get a new copy of the current kernel? Of course I would really like to keep a copy of the old kernel as well, since it is the only thing which still works.
I have already changed the activity of the lid closing so that it will no longer suspend, but will Shut down. Suspend is just too drastic an action for this HP machine. I don't know why, I just know to avoid it....

Thanks,
Ilan

---

### Post by .... on 2011-09-19
Boot into the old kernel and purge/completely remove the current kernel (at least the linux-image package for that kernel). It's easiest to do this in synaptic.

---

### Post by ilantal on 2011-09-19
Thanks, as I had never done such a thing. I asked for reinstallation of 3 files with 2.6.38-11 where I booted with 2.6.38-8. One was headers, one was the linux image and I forgot what the 3rd was, but it was 2.6.38-11.

Unfortunately it still doesn't boot under the reinstalled 2.6.38-11 and I still have to drop back to 2.6.38-8. So my question is: if it isn't the kernel, what else could it be? What the best/easiest or whatever, method to get the system up and flying under the current kernel?

Thanks,
Ilan

---

### Post by ilantal on 2011-09-20
I don't know what exactly happened but when I tried to boot on this morning, Ubuntu came up with 2.6.38-11. Apparently after the first unsuccessful attempt, Ubuntu managed to fix itself. Anybody have any suggestions as to what happened and why I saw the failure after the first reinstall and "Reboot to complete install"?

In any case it now seems to be up and flying.

Thanks,
Ilan

---

