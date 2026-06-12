---
title: "Installing from USB, still asks for CD"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by Ochobobo on 2009-10-12
I'm trying to install Ubuntu Studio 9.04 on my old desktop, although so far I've been unsuccessful. First I tried burning the iso to a DVD and tried booting from that, but I ended up with a "cannot mount CD" error during the installation. I did a Google search and found that Ubuntu doesn't seem to like some old CD drives. I figured mine must be one of them.

So I tried extracting the iso to my usb drive using unetbootin. I then set the bios on my desktop to boot from usb, and the installation started. However, for some unknown reason I still ended up with the exact same error as before. It's still telling me it "cannot mount CD" even though I'm booting from USB and every other boot option has been disabled. Even with the burned DVD out of the computer, it's still giving me that error.

Just so you know, I'm completely new at using any Linux distro, so it's very possible I'm missing some obvious solution here.

Any ideas?

---

### Post by Lars Noodén on 2009-10-12
Have you set a default choice in grub and shortened the timeout for it?
e.g.
```

default         0
timeout         3

```

---

### Post by wscheun on 2009-11-06
I'm having the same problem, booting from USB goes fine, it asks for language and keyboard setup, and then it wants a CD-ROM driver. What to do?

---

### Post by xandionthedrums on 2009-11-27
does anybody know how to solve this?
even if I mount my usb-drive to */cdrom* the installer doesn't accept it

---

