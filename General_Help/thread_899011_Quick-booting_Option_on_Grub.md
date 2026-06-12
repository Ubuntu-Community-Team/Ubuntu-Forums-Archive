---
title: "Quick-booting Option on Grub?"
date: 2008-08-23
forum: General Help
---

### Post by Origin on 2008-08-23
Hey guys,

I run 64 bit Hardy with GNOME on my Thinkpad T61 and I'm wondering if there's anything I can do to have a quick-booting option in Grub in the case that I want to open a document or fire off an email and only have 30s or so to wait for the OS to boot up.

Is there any way to add an option to GRUB that loads only the bare essentials? Say, just a desktop with Firefox or something--don't need rsync, ALSA, cron, etc. I don't mind if the desktop becomes a bit uglier. I won't be using this very often anyway.

Any ideas?

Thanks,
Jinghao

---

### Post by prshah on 2008-08-23
> **Origin said:**
> 
Is there any way to add an option to GRUB that loads only the bare essentials? 

Nope GRUB cannot do this; but there is a way...

Install Puppy, Slitaz or DSL (in order of recommendation), and setup grub to boot that distro when you want a quick up and down.

---

### Post by Patb on 2008-08-24
Origin, another possible solution is to trim out unnecessary processes started during boot.  A helpful guide can be found [here]("http://ubuntuforums.org/showthread.php?t=89491")

Hope this helps. Cheers, Pat.

---

