---
title: "[GRUB] Too many booting options..."
date: 2008-07-31
forum: General Help
---

### Post by DivinityX on 2008-07-31
When i start my computer, i get something like this in the boot menu...

UBUNTU 8.04 - 19    <----I get a blank white screen aftre login
UBUNTU 8.04 - 19 Recover
UBUNTU 8.04 - 18    <----This is the one i'm running right now
UBUNTU 8.04 - 18 Recover
UBUNTU 8.04 - 17    <----Untested
UBUNTU 8.04 - 17 Recover
UBUNTU 8.04 - 16    <----Untested
UBUNTU 8.04 - 16 Recover
Mem test
Other OS:
Windows XP (loader)
Windows XP Home Edition

I don't understand why the others are up there, and i wanna know what i should do to take them off the list...

---

### Post by damis648 on 2008-07-31
Uninstall the linux-image-(option you do not need) package from synaptic. I would try to fix your -19 kernel if i were you. Could you give more details on the white screen? Any Panels? Login Screen?

---

### Post by drs305 on 2008-07-31
Each time a new kernel is introduced it is added to menu.lst You can remove extra kernels via synaptic and they will be removed from the menu as well. Look for the linux-image-2.XXXXX 

Make sure to keep your good one and it's good to keep a backup. This will ensure you know what kernel you are running.
```
uname -r
```

You can also make lots of changes to menu.lst with a gui app called StartUp-Manager. Go to the link in my signature to read about it. It's a good app for making changes safely and you can set which kernel to use on boot.

---

### Post by Diabolis on 2008-07-31
Every time you do a kernel upgrade, usually a ubuntu version update, the update version is added to the menu.lst file and the old ones are kept.

You just have to delete them.
```
sudo gedit /boot/grub/menu.lst
```

---

### Post by Pacopag on 2008-07-31
Has it always been like this?
I had a similar problem once, and I think it was caused by an error that happened during an update (kernel maybe).  I just booted into the second one, like you did, then re-ran the update and it fixed it up.  I still have a long list of booting options upon startup, but I only ever need to use the first one (ubuntu) and the last one (windows).

Sorry if I'm not making sense, or if I'm just stating things that are painfully obvious.  I'm still very new to linux and dual booting.

---

### Post by drs305 on 2008-07-31
> **Pacopag said:**
> I still have a long list of booting options upon startup, but I only ever need to use the first one (ubuntu) and the last one (windows).

Sorry if I'm not making sense, or if I'm just stating things that are painfully obvious.  I'm still very new to linux and dual booting.

You can remove any of the kernels you don't need by removing the extra linux-image-2.6.24-XX via synaptic. You can also limit the number you see in StartUp-Manager, but they won't be removed from your computer (only from the menu). SUM also has an option to choose which OS you want to boot as default, should you ever want to change it.

---

### Post by DivinityX on 2008-07-31
> **damis648 said:**
> Uninstall the linux-image-(option you do not need) package from synaptic. I would try to fix your -19 kernel if i were you. Could you give more details on the white screen? Any Panels? Login Screen?

When i log in, i hear the start up tune and see a white screen. i'm able to move the mouse but there is nothing to click. i let it set for about half an hour..nothing...


> **drs305 said:**
> Each time a new kernel is introduced it is added to menu.lst You can remove extra kernels via synaptic and they will be removed from the menu as well. Look for the linux-image-2.XXXXX 

Make sure to keep your good one and it's good to keep a backup. This will ensure you know what kernel you are running.
```
uname -r
```

You can also make lots of changes to menu.lst with a gui app called StartUp-Manager. Go to the link in my signature to read about it. It's a good app for making changes safely and you can set which kernel to use on boot.

ok, i'll try this...

---

### Post by DivinityX on 2008-07-31
Should i check for Removal or Complete Removal?

---

### Post by Diabolis on 2008-07-31
Same thing, removal should be fine for a kernel image.

---

### Post by DivinityX on 2008-07-31
Thank you guys! I was able to remove them, i also set 19 to reinstall. if i still have problems with it, i'll throw up a thread about it! ^_^

[SOLVED!!]

---

