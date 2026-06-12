---
title: "i had a powercut last night, now my computers kindof broke..."
date: 2008-10-25
forum: General Help
---

### Post by joesoaps on 2008-10-25
im running ubuntu 8.04, and im a noob so bare with me.
i start up my computer, the part where "ubuntu" is on the screen comes up and its loading comes up,
then this pops up

Starting up...
Loading, please wait.
kinit: name_to_dev_t (/dev/disk/by-uuid/39a8cd5c-de5b-46b3-9607-d2d108124147) = sda5(8,5)
kinit: trying to resume from (/dev/disk/by-uuid/39a8cd5c-de5b-46b3-9607-d2d108124147
kinit: No resume image, doing normal boot...
Ubuntu 8.04.1 joe-destop tty1
joe-desktop login:

i logged in like that, but just loads of jibberish comes up, nothing important.

what can i do to get my computer up and running like it was before?

---

### Post by louieb on 2008-10-25
Sounds like X isn't starting. Try booting into recovery mode and run **xfix**.

---

### Post by joesoaps on 2008-10-25
how do you boot in recovery mode?

---

### Post by Dr Small on 2008-10-25
> **joesoaps said:**
> how do you boot in recovery mode?
From the GRUB prompt, choose Recovery Mode.

---

### Post by joesoaps on 2008-10-25
i worked out how to boot in recovery mode, i done what you said but the same thing is still happening.

---

### Post by Dr Small on 2008-10-25
What about trying this from Recovery Mode?
```
dpkg-reconfigure -phigh xserver-xorg
```

Of course, you could just add sudo, and run it from your own prompt.

---

### Post by joesoaps on 2008-10-25
> dpkg-reconfigure -phigh xserver-xorg
i put that in, it says:

xserver-xorg postinst warning: overwriting possibly-customized configurration
file; backup in /etc/X11/xorg.conf.20081025134423

---

### Post by louieb on 2008-10-25
Thats the normal message.  Not going to break it any worse that it all ready is. And just might fix it. If not believe recovery has an option to fix a broken system. I haven't had to use it yet  so not any help with it.

---

