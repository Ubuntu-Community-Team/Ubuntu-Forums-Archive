---
title: "Multiple OS load?"
date: 2009-03-16
forum: Installation &amp; Upgrades
---

### Post by mrdolphin on 2009-03-16
Hiya. I am starting to use Ubuntu much more recently and I noticed after I updated Ubuntu, when I boot up my computer to the OS loading page (Dual booted with Vista), I see about 10 different Ubuntu choices (some have recovery mode next to it). How do I get rid of these excess options? Im reformatting my computer (for other reasons) and installing Ubuntu again.

Thanks in advance!

---

### Post by taurus on 2009-03-16
You only have one release.  However, you have multiple kernels so if you want to keep only one kernel, the latest, go into synaptic and **Search** for linux-image.  Then, remove the old ones.

Now, have a look at /boot/grub/menu.lst to see if the entries for the old kernels are still in there.  Remove them if they are.

```
gksudo gedit /boot/grub/menu.lst
```
If you want to limit the numbers of kernels on your machine, install startupmanager and use it to configure it.

```
sudo apt-get update
sudo apt-get install startupmanager
gksudo startupmanager
```

---

### Post by mrdolphin on 2009-03-16
Thanks a lot! Ill try it when I finish formatting my comp. So fast ;)

---

### Post by davec64 on 2009-03-16
> **mrdolphin said:**
> Hiya. I am starting to use Ubuntu much more recently and I noticed after I updated Ubuntu, when I boot up my computer to the OS loading page (Dual booted with Vista), I see about 10 different Ubuntu choices (some have recovery mode next to it). How do I get rid of these excess options? Im reformatting my computer (for other reasons) and installing Ubuntu again.

Thanks in advance!


Open up Synaptic and search for Linux Image
Right click and mark the older ones for removal.

It's a good idea to keep at least 2 versions of the Kernel just in case you have problems with one! At least that way you can get into the system.

I can't remember if by removing the kernel images the Grub list gets updated, do if it doesn't you might need to go into it and remove the corresponding entries.

All the best

---

