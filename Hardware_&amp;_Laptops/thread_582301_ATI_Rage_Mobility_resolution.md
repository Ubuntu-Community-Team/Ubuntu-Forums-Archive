---
title: "ATI Rage Mobility resolution"
date: 2007-10-19
forum: Hardware &amp; Laptops
---

### Post by scurvy on 2007-10-19
While trying to run the recommended quick fix from Ubuntu, i receive the following error:

josh@josh-laptop:~$ aticonfig --initial --input=/etc/X11/xorg.conf
Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.original-0
aticonfig: Writing to '/etc/X11/xorg.conf' failed. Bad file descriptor.

suggestions are appreciated.

Josh

---

### Post by googlah on 2007-10-20
Hey, I can't say why it's not working, but you could try typing
```
sudo dpkg-reconfigure xserver-xorg
``` in the terminal. In the very last questions you are allowed to mark which resolutions you want to be able to choose from. Hope this helps.

Greets from Sweden.

---

### Post by scurvy on 2007-10-22
Hi Googlah,
You're awesome! Ran the reconfig, taking the defaults and it worked like a charm!!

Thanks a bunch!

I posted another issue trying to convert my desktop to Ubuntu regarding a video issue probably. Maybe you could take a look at that as well.

Josh

---

