---
title: "[SOLVED] Does someone know how to fix Grub error 22?"
date: 2008-08-20
forum: General Help
---

### Post by Aeph on 2008-08-20
Recently, I helped a friend of mine dual-boot Ubuntu on his new laptop. However, we ran into issues with the internet connection and decided to remove it. Now he receives a "Grub error 22" when he starts up the system and can't load Windows Vista. I believe that Grub 22 is when the BIOS attempts to load the Grub bootloader, but it isn't there and doesn't know what to do.

The only way I know of to fix this is to reinstall Ubuntu in a really small partition and ignore it, but I'm hoping there is a better way. Please help.

---

### Post by alynx on 2008-08-20
could this help ?

[http://support.microsoft.com/kb/69013](http://support.microsoft.com/kb/69013)

---

### Post by angry_johnnie on 2008-08-20
You would need a Windows installation cd.
With XP, what you did was insert the cd, boot in recovery mode, and then type

```
FIXBOOT
```

and
```

FIXMBR
```

If you don't have a Windows installation cd.  [This]("http://ubuntuforums.org/showthread.php?t=622828") could probably do it.  The only problem is that ms-sys is not available in Hardy repos.  You'd either have to use an older ubuntu cd, or download it [here]("http://packages.ubuntu.com/gutsy/ms-sys"), install it on the live cd, and then do the ms-sys --mbr thing.

---

### Post by caljohnsmith on 2008-08-20
> **angry_johnnie said:**
> You would need a Windows installation cd.
With XP, what you did was insert the cd, boot in recovery mode, and then type

```
FIXBOOT
```

and
```

FIXMBR
```

If you don't have a Windows installation cd.  [This]("http://ubuntuforums.org/showthread.php?t=622828") could probably do it.  The only problem is that ms-sys is not available in Hardy repos.  You'd either have to use an older ubuntu cd, or download it [here]("http://packages.ubuntu.com/gutsy/ms-sys"), install it on the live cd, and then do the ms-sys --mbr thing.
Actually, "fixboot" and "fixmbr" are only for Windows XP--they won't help you fix a Windows Vista MBR problem.

Aeph, here's a [step-by-step guide of how to recover your Windows Vista MBR]("http://neosmart.net/wiki/display/EBCD/Recovering+the+Vista+Bootloader+from+the+DVD"). It even has a link at the beginning of where you can download a Windows Vista Recovery CD in case you don't all ready have one.

---

### Post by Aeph on 2008-08-29
Thanks for the help. Forgot to mark the thread as solved until now. One last question: if I were to not install the GRUB and then removed the partition or drive, would this prevent these errors from happening, or would it just cause new ones?

---

### Post by caljohnsmith on 2008-08-29
> **Aeph said:**
> Thanks for the help. Forgot to mark the thread as solved until now. One last question: if I were to not install the GRUB and then removed the partition or drive, would this prevent these errors from happening, or would it just cause new ones?
I think if you don't install Grub in the first place, you certainly won't get any Grub errors when you delete your Ubuntu partition. ;)

---

