---
title: "Removing Linux header"
date: 2008-11-05
forum: General Help
---

### Post by And6ate9 on 2008-11-05
I know this has been asked over and over again but the fixes dont see to be working for me. I have look for the headers in synaptec but I do know see the one that seem to be loading in grub some of them say server or rt or openvz at the end. How do I get rid of these suckers

---

### Post by Kevbert on 2008-11-05
What are you trying to remove ? the unused kernels (e.g. 2.6.24-19) used in the grub boot menu ?

---

### Post by cariboo on 2008-11-05
In Synaptic search for:

```
linux-image-2.6.xx-XX
```

Where xx is the point version and XX is the type eg:
sever, generic, virtual and rt.

Make sure you don't completely move the kernel you are using now. This will also remove the menu entry in grub. If you have already removed the unused kernels, you can just remove them from grub. To edit grub, press Alt-F2 and type:

```
gksu gedit /boot/grub/menu.lst
```

Note: It would be a goog idea to make a backup copy of /boot/grub/menu.lst first before making any changes. Open a Applications-->Accessories-->Terminal and type:

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
```

Jim

```

```

---

### Post by And6ate9 on 2008-11-05
OK this is very weird in grub I see at least 4 old kernal version that dont seem to show up in synaptic. They are also in my boot directory. Is it save to assume I can delete these references in my boot and grub with no trouble?

---

### Post by Rainstride on 2008-11-05
> **And6ate9 said:**
> OK this is very weird in grub I see at least 4 old kernal version that dont seem to show up in synaptic. They are also in my boot directory. Is it save to assume I can delete these references in my boot and grub with no trouble?

use system cleaner, is in the repos, works perfect for this.

---

### Post by chenel on 2008-11-05
If I were you I'd run
```
sudo update-grub
```
first and see if they disappear.  If you've installed all the kernel versions you have via Synaptic, this should get rid of any extras.  If it doesn't, then you might want to check for the corresponding version numbers in /boot before you go deleting things willy-nilly...  update-grub is usually pretty smart about finding old kernels :)

---

### Post by Kevbert on 2008-11-06
It's probably worth keeping at least one old kernel in case of problems. You can get rid of the old kernels with Synaptic. Just search for linux-image and then do a complete removal of the relevant linux-image-2.6...-generic files.

---

### Post by And6ate9 on 2008-11-06
I see all of the headers in the boot folder but non are in synaptic.

The system cleaner did not work. All it did was remove my opera.deb

Could those headers be there cuz I am uing Virtualbox? or a bad upgrade from hardy?

---

