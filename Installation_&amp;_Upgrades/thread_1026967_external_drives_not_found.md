---
title: "external drives not found"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by \george Woodward on 2008-12-31
Just installed Xbuntu 8.04 on Dell L400 laptop Pentium 3 600mhz 256mb ram 8 gig hard disk using compete disk (was w2000). Smooth installation and working OK BUT cannot see external cd drive or USB memory stick. I  have set authorizations but no change.I  Probably something obvious I am missing?

I could not find a way to uninstall Xbuntu so

Thought I would load Ubuntu to delete Xbuntu so set bios to boot from Ubuntu CD=which is does but ends up back with Xbuntu .Grub file confusion ?

---

### Post by Bucky Ball on 2009-01-25
Xubuntu is Ubuntu but with Xfce desktop manager instead of Gnome. Some of the packages are also different. The best way to uninstall is go to Synaptics and search for 'xubuntu-desktop'. You can install Ubuntu by searching for 'ubuntu-desktop'. Grub file makes no difference. Still booting the same kernel, different desktop manager.

---

### Post by taurus on 2009-01-25
If you want to use Gnome, just install it from a terminal.

```
sudo apt-get update
sudo apt-get install ubuntu-desktop
```
Then, you can remove XFce4 if you think Gnome is working fine on your slow machine.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

And a USB device doesn't automount when you plug it in, you can still mount it from a terminal.  Plug one in and post the output of this command from a terminal.

```
sudo fdisk -l
```

---

