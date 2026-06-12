---
title: "Installing on laptop ? Booting from USB ?"
date: 2010-05-14
forum: Hardware
---

### Post by Mongao on 2010-05-14
Hi all,

I have just bought a HP laptop that comes with Windows 7, I am afraid of installing Ubuntu on it and damage the factory-made Windows installation; I`m pretty used to installing Ubuntu in dual-boot on regular desktops.

Please, is there any special recommendation when installing Ubuntu in a laptop ? is there any kind of special "Ubuntu for laptops" edition ?

Is it possible to BOOT Ubuntu from a USB key ? I mean, the laptop BIOS would serach for the first boot device and I would set it to look first to a USB key, and then Ubuntu would boot from there. is it possible ? 

Thanks,
Mongao

---

### Post by johndharvey on 2010-05-14
> **Mongao said:**
> Hi all,

I have just bought a HP laptop that comes with Windows 7, I am afraid of installing Ubuntu on it and damage the factory-made Windows installation; I`m pretty used to installing Ubuntu in dual-boot on regular desktops.

Please, is there any special recommendation when installing Ubuntu in a laptop ? is there any kind of special "Ubuntu for laptops" edition ?There is a version of Ubuntu made especially for small laptops.  It's called Ubuntu Netbook Remix.

> Is it possible to BOOT Ubuntu from a USB key ? I mean, the laptop BIOS would serach for the first boot device and I would set it to look first to a USB key, and then Ubuntu would boot from there. is it possible ?
Yes, absolutely.  You can find instructions for doing that on Pendrivelinux.com, where you can download a utility for making a bootable Linux USB drive on Windows.  Just download it and follow the prompts.  The utility lets you select which distro you want to install, and which USB device you want to use.  If you want to keep your changes from one session to the next, then you'll want to include some persistence.  When you boot your computer, on the very first screen that shows up (usually with the name of your computer's manufacturer), there should be some options at the bottom.  One of them should be something like "F12 - hardware boot options".  That's the one you want.  The next screen should be a list of hardware devices, such as your hard drive and your USB drive.  Naturally, you want to select your USB drive.  After that, just follow the prompts and wait.  It generally takes a little while longer to boot from a USB than it does to boot from the hard disk, but everything should work just the same once it loads.

---

### Post by Mongao on 2010-05-15
Thanks John, I`ll take a look.

Regards,
Mongao

---

