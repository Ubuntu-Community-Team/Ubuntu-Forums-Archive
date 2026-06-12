---
title: "[SOLVED] Package installation problems in a low memory system"
date: 2008-12-07
forum: Installation &amp; Upgrades
---

### Post by Terraman on 2008-12-07
Dear Ubuntu friends,

I've successfully installed Ubuntu 8.10 command line system in a Compaq Armada 1571 DM, MMX, 200 MHZ, and 64 MB memory.

Now, I'm trying to install a lightweight system.

I can't install packages with "apt-get" or "aptitude", because this computer doesn't have an Internet connection. In addition, the offline installation using the package APTonCD fails too.

So, I downloaded the xorg package, copied it to the laptop, untar it, and when I run ./configure in order to install x.org, I've got this message: "configure:3753: error: no acceptable C compiler found in $PATH".

Can someone help me? What shall I do?

Thanks in advance!

---

### Post by taurus on 2008-12-07
You need gcc compiler before you can compile anything from source.  The build-essential package is on the installer CD.  Insert it and run (from a terminal)

```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install build-essential
gcc -v
```

p.s.  Good luck trying to run Gnome with that little RAM.

---

### Post by Terraman on 2008-12-07
Thank Taurus,

Yes, you'll right, let's see what happens.

---

