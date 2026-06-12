---
title: "[SOLVED] Question about Clean install of 8.10"
date: 2008-12-29
forum: Installation &amp; Upgrades
---

### Post by redonwhite on 2008-12-29
Im planning on upgrading 8.04 to 8.10.  I spent some time over the summer figuring out how to install XP on one Hard Drive and Ubuntu on my other Hard drive so that i could pick what operating system to use when i boot up.  I was curious if i do a clean install of 8.10 will that mess up Grub at all?  Right now when i boot up my computer i get a screen that ask me if i want to either boot XP or Ubuntu  ( anyone know why Ubuntu is listed 4 times on this screen with Recovery mode underneath each listing of Ubuntu?  if so how does one get rid of this?).  I didn't want to mess up this configuration i have set up because honestly i don't remember how the heck i got it to work.

---

### Post by Partyboi2 on 2008-12-29
If you are going to do a clean install of Ubuntu it will install grub and add your windows to the grub menu just as it is now.
> anyone know why Ubuntu is listed 4 times on this screen with Recovery mode underneath each listing of Ubuntu? if so how does one get rid of this?This happens when the kernel gets upgraded, you can either remove your old kernels (search for linux-image in synatpic) that you know longer need (always good to keep at least one  as a backup) Or you can change the ```
howmany=all 

``` option in your grub menu.lst to hide the ones you don't want  displayed.
eg.
```
howmany=4
```

---

### Post by redonwhite on 2008-12-29
Thank you for the information.  When i install 8.10 will it list both hard drives, with each labeled which one has XP on it and which one has 8.04 on it?  That would stink if i accidentally installed 8.10 over my xp drive hehe =).

---

### Post by mikewhatever on 2008-12-29
Yes, it should, so be careful.

---

### Post by redonwhite on 2008-12-29
> **mikewhatever said:**
> Yes, it should, so be careful.

Okay.  Thank you. =)

---

### Post by Partyboi2 on 2008-12-29
You can also check what partition windows is on before installing by opening a terminal and typing
```
sudo fdisk -l
``` Then take note of what partition is ntfs or fat and then when you are installing you will know what partition is what.

---

