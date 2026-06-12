---
title: "Availability of the terminal?"
date: 2009-04-05
forum: Installation &amp; Upgrades
---

### Post by daigu on 2009-04-05
I have another post on this forum regarding my problems with GRUB, and I've noticed that in a lot of posts, answers have some reference to the "terminal" in it. Now I'm booting from a CD with the ubuntu-8.10-server-amd64.iso on it, and I haven't seen any GUI with a menu (Applications->Accessories...) on it. Haven't seen a GUI at all, except for the install screen.

I'm assuming that I should be able to get a menu without a proper install, otherwise all those other people wouldn't be able to access their terminal either. So now I'm wondering whether I'm using the wrong CD. So far I've only seen the Desktop/LIVE CD mentioned.

Can anyone enlighten me on this point?

---

### Post by issih on 2009-04-05
The ubuntu server edition doesn't come with a gui installed by default. The terminal is exactly what you are seeing, the command prompt.

The desktop version comes with the gnome desktop environment, and then you launch a little terminal window to access the command line.

If you need a gui in the server edition, you need to get connected to the internet, then enter:

```
sudo apt-get install ubuntu-desktop
```

in order to install the necessary packages.

Hope that helps

---

