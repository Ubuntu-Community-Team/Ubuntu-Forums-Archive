---
title: "how is xorg used in ubuntu?"
date: 2008-07-25
forum: General Help
---

### Post by cwacker on 2008-07-25
Where can i read documentation about how X is used in ubuntu? If I cat /etc/X11/xorg.conf i get weird results, where device and monitor sections does'nt contain the usual stuff and so on? I'm wondering because my display works wonderfully in ubuntu and I want to se how it X is configed to give the marvelous output it does...

---

### Post by decoherence on 2008-07-25
try running

Xorg -configure

that does the normal autodetection and should output a more familiar file. i think you'll have to stop the x server and run the command with sudo

---

### Post by cwacker on 2008-07-25
So Ubuntu simply uses the auto configure when configuring the xserver?

---

### Post by pietjanjaap on 2008-07-25
This how you adjust your videocard and monitor. The keybord is the old way.

With ubuntu 8.04, dpkg-reconfigure xserver-xorg (old way)is not the same anymore, now you can install your keybord and more with this.
But your videocard and monitor goes like this,
start in safe mode,
choose the last options with the "Try to fix X-server",(new way)
Here ubuntu will search and identify your monitor and videocard, so you have all your posssible settings.
Then reboot and install your videcard driver.(i use envy for this).

---

### Post by cwacker on 2008-07-25
I thikn you misunderstood me.
I do not want to reconfigure the xserver, i just want to se it's current settings and they are not displayed in xorg.conf in my X11-dir.

---

### Post by coffeecat on 2008-07-25
> **cwacker said:**
> Where can i read documentation about how X is used in ubuntu? If I cat /etc/X11/xorg.conf i get weird results, where device and monitor sections does'nt contain the usual stuff and so on? I'm wondering because my display works wonderfully in ubuntu and I want to se how it X is configed to give the marvelous output it does...

Xorg is working more and more towards autodetection so that you need less stuff in xorg.conf. If you're comparing the xorg.conf with that in another distro, the chances are that the other distro is using an earlier version of xorg. I believe the eventual aim is to be able to do without xorg.conf in most cases.

If you think the Ubuntu xorg.conf is small, have a look at a Fedora one. :-k

---

