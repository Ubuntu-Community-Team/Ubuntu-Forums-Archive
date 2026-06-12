---
title: "Problems with XServer after upgrading to herdy 8.10"
date: 2008-11-29
forum: General Help
---

### Post by kokkus on 2008-11-29
Hey.
I had this problem when I upgraded from 7.10 to 8.04 as well, but I can't remember how I fixed it. I think I asked for help in the forum.

After I resterted the pc after the upgrade I got the message that there was some problems with the xserver, so I couldn't access gnome.
I went to recovery mode and fixed the x server and went back into the operating system and enabled the graphic driver again.
But the problem is now that the xserver error message came up again when I restarted the PC.
I hope someone could help me with this.
Thanks in advance:)

---

### Post by merlin666 on 2008-12-02
Did you find a solution for this problem yet?

---

### Post by kokkus on 2008-12-03
Nope, not yet.
Plz help me out here.
Things I've tried is not much. Reinstalling and repairing the x server. Now I am where I was when I asked for help the first time.

---

### Post by sedawk on 2008-12-03
This can happen with the nvidia driver, even using a failsafe xorg.conf
will still load nvidia modules that fail to start (glx?).

Have a look at the error messages (/var/log/Xorg.log) and then
use them to search for a solution with your favourite search engine.

In case you are using Nvidia a good start might be to deinstall the
packages that bring the nvidia files.
(e.g. "dpkg -S glx")

---

### Post by kokkus on 2008-12-03
Deinstall? You mean reinstall them in the package manager or remove them, reboot and install them again?

---

### Post by sedawk on 2008-12-04
I do it from command line, e.g. something like
```

dpkg -l |grep -i nvidia

```

then to remove a package

```

sudo apt-get remove mypackage

```

Afterwards try restarting X-Server

```

sudo /etc/init.d/gdm restart

```

Rebooting should be necessary.

---

