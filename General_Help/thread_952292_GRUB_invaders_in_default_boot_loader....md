---
title: "GRUB invaders in default boot loader..."
date: 2008-10-19
forum: General Help
---

### Post by Animeniac on 2008-10-19
I have just installed GRUB invaders, but I didn't install "grub-pc". There is no boot option for it. I thought there would be...

How do I add GRUB invaders as a boot option in the default boot loader?

---

### Post by Pro-reason on 2008-10-19
Yes, perhaps the grub-invaders package should have a post-installation script that sets that up.  Maybe I'll write one.  

Anyway, do this:

```

dpkg -L grub-invaders

```

That will give you a list of all the files installed by the package.  The following should be of interest:

```

cat /usr/share/doc/grub-invaders/README
cat /usr/share/doc/grub-invaders/examples/grub-menu.lst

```

This documentation essentially says that you need to add a line somewhat like this:

```

title   GRUB Invaders
root    (hd0,0)
kernel  /boot/invaders

```

---

### Post by Animeniac on 2008-10-22
Thanks for your help, Pro-reason. I added this in the menu.lst file: ```
title	GRUB Invaders
root	(hd2,5)
kernel	/boot/invaders
```

Even though I never tried it, it should work.

---

### Post by Herman on 2010-05-01
:) This old thread needs an update!

It's much easier to install grub-invaders now.
All we need to do is give the command,
```
sudo apt-get install grub-invaders
```That command will automatically install grub-invaders and add it to our boot menu in GRUB2, so all we need to do is reboot, select grub invaders and start playing! :)

:guitar:

---

