---
title: "Help installing Ubuntu 8.10 on Tyan S2892  mobo"
date: 2009-03-26
forum: Installation &amp; Upgrades
---

### Post by GhostLine on 2009-03-26
been searching google for hours now and so far nothing came up that has the same problem as mine.

Im installing Intrepid live cd on the following specs
Mobo: Tyan S2892
CPU: AMD Opteron 280
Memory: 2 x 512MB Corsair
Video Card: Geforce 8400S
Hard Drive: 400GB Western Digital SATA

When i tried installing, removing the "quiet splash" option. The installation hangs after this msg

[0.625023]PCI: Using configuration type 1 for base access 

I just have a blinking dos cursor after that


haven't tried yet alternate cd install, since im not yet finish downloading

---

### Post by spcwingo on 2009-03-26
I had a problem installing on a Tyan board [S2518].  I had to use the mini CD to install.  The mini CD can be found here:

[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

Make sure you are connected to your router/modem via ethernet cable before booting the CD.  At the boot prompt enter:

```
cli noapic acpi=off
```

Follow the prompt to install the base system and reboot when prompted.  After the reboot your system will boot into a command line system only.  Log in (when typing your password you won't see any "*", this is normal) and type one command:

```
sudo apt-get install ubuntu-desktop
```

Enter your password when prompted.  This will install the standard Gnome desktop.  When it gets done type:

```
sudo apt-get clean && sudo reboot
```

This will clean your apt cache and reboot into your new Ubuntu desktop.  Bear in mind that the ACPI will not work, so when shutting down it won't turn itself off, when the progress bar reaches the end just press the power button.  I also will not guarantee this will work for you, but it did work in my case.

---

