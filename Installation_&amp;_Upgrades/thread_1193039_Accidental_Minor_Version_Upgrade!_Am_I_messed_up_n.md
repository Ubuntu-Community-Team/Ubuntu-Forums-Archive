---
title: "Accidental Minor Version Upgrade! Am I messed up now?"
date: 2009-06-21
forum: Installation &amp; Upgrades
---

### Post by mtheultimate on 2009-06-21
I have only been using Ubuntu for a couple weeks now. Trying to upgrade
Pidgin, I went into Synaptic and did "Mark Upgrades" and applied, then restarted.
Now my boot screen has:

ubuntu 2.6.28-13
ubuntu 2.6.28-13 ...
ubuntu 2.6.28-11
ubuntu 2.6.28-11 ...

I didnt mean to update the minor version (I just wanted to update Pidgin). 
Should I just hide it in the boot menu, or is there a safe uninstall? Did I just make a huge mistake?

---

### Post by jocko on 2009-06-21
> **mtheultimate said:**
> I have only been using Ubuntu for a couple weeks now. Trying to upgrade
Pidgin, I went into Synaptic and did "Mark Upgrades" and applied, then restarted.
Now my boot screen has:

ubuntu 2.6.28-13
ubuntu 2.6.28-13 ...
ubuntu 2.6.28-11
ubuntu 2.6.28-11 ...

I didnt mean to update the minor version (I just wanted to update Pidgin). 
Should I just hide it in the boot menu, or is there a safe uninstall? Did I just make a huge mistake?
Why would it be a mistake to install an update? The reason they release updates is that they have solved a problem with the old version.
If you want to get rid of the extra kernel in the boot menu, just uninstall it (the package name is linux-image-2.6.28-11-generic).

---

### Post by cybergalvez on 2009-06-21
> **mtheultimate said:**
> I have only been using Ubuntu for a couple weeks now. Trying to upgrade
Pidgin, I went into Synaptic and did "Mark Upgrades" and applied, then restarted.
Now my boot screen has:

ubuntu 2.6.28-13
ubuntu 2.6.28-13 ...
ubuntu 2.6.28-11
ubuntu 2.6.28-11 ...

I didnt mean to update the minor version (I just wanted to update Pidgin). 
Should I just hide it in the boot menu, or is there a safe uninstall? Did I just make a huge mistake?

don't worry about it kernel updates don't happen very often, but when they do it a good idea to install them

---

### Post by mtheultimate on 2009-06-21
Thanks. In my case, audio doesnt work in the upgrade. I'm guessing I have to recompile the
audio driver for my sound card? What other things do I have to redo? Do I have to re-enable all
the repositories that I've added?

I went through a lot to get Ubuntu to work, I don't think I have it in me to do it all over again 2 weeks later. :)

---

### Post by jocko on 2009-06-21
> **mtheultimate said:**
> Thanks. In my case, audio doesnt work in the upgrade. I'm guessing I have to recompile the
audio driver for my sound card? What other things do I have to redo? Do I have to re-enable all
the repositories that I've added?

I went through a lot to get Ubuntu to work, I don't think I have it in me to do it all over again 2 weeks later. :)
You shouldn't need to redo anything. It was just a kernel update, it didn't change anything else than the actual kernel.
If you by some reason had compiled a sound card driver for the old kernel, then you may need to compile it again for the new kernel.
Why don't you trust the ubuntu developers? If they release an update, it's because they have fixed a problem with the old version of the package. A kernel update just gives you a new kernel, a pidgin update just gives you a new version of pidgin and a firefox update just gives you a new version of firefox. None of them replaces your repositories, and none of them will try to delete any of your data. Relax.

---

### Post by mtheultimate on 2009-06-21
> 
Relax.
I think you are misreading my posts? :) 
I am relaxed and I have a very good reason to ask whether I need to re-enable my repositories. 
Most repository sites say something like the Pidgin notice below:

> 
Once this PPA is setup, Pidgin updates will show up in Update Manager along with the usual Ubuntu updates. **The PPA will need to be re-setup only after upgrading Ubuntu.**
I'm new at this so I dont know if that means major version upgrades only or if that includes minor versions.
Thats why I asked. I trust the Ubuntu developers, but with only 2 weeks on Linux, I don't really trust myself.
Thanks.

---

### Post by jocko on 2009-06-22
> **mtheultimate said:**
> I think you are misreading my posts? :) 
I am relaxed and I have a very good reason to ask whether I need to re-enable my repositories. 
Most repository sites say something like the Pidgin notice below:

I'm new at this so I dont know if that means major version upgrades only or if that includes minor versions.
Thats why I asked. I trust the Ubuntu developers, but with only 2 weeks on Linux, I don't really trust myself.
Thanks.You have not upgraded ubuntu, just installed a kernel update.
If you are used to windows terminology it's like you have installed a simple security update which fixes a problem in the file ntoskrnl.exe (which I think is the windows kernel). That probably happens very often without the windows users noticing much. What you are worried about would be more like upgrading from XP to Vista, when you would have to make sure all your third party software is vista-compatible.
If you upgrade to the next version of ubuntu (9.10, Karmic Koala, which will be released in october. That's an upgrade of every one of the ~1500 installed packages), you will have to change your 3rd party repositories manually afterwards, as the upgrade process will not do that automatically.

---

