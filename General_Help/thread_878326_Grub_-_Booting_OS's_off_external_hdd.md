---
title: "Grub - Booting OS's off external hdd?"
date: 2008-08-02
forum: General Help
---

### Post by kachofool on 2008-08-02
Hey all,

How would I go about booting another OS (Vista, Ubuntu, , another Linux distro, OS X, etc) off an external USB hard drive?

In particular when I make the entry for GRUB, I'm not sure what I specify for the root address. How does GRUB resolve the external hdd address?

I only have one internal hdd, and my system supports booting from USB.

If my internal is simply (hd0) then is the USB one automatically (hd1)?

TiA,

KF

---

### Post by logos34 on 2008-08-02
> **kachofool said:**
> 
If my internal is simply (hd0) then is the USB one automatically (hd1)?


yes.  So if the root of the other OS is the first partition on the usb drive, the entry in menu.lst should be:

root (hd1,0)

---

### Post by redraiderbum on 2008-08-02
If I want to boot to an external device then I generally put the boot loader on the external device immediately following installation.  Then it is a simple matter of telling bios to boot to that device.

Also I believe linux registers external drives as sata drives.  You could check on that with fdisk and seeing what the name of the device is in /dev

---

### Post by logos34 on 2008-08-03
Do you already have linux on the internal (what I assumed--perhaps wrongly)?  If not, you'll want to do what redraiderbum suggested and put the grub bootloader on the MBR of the external usb and boot directly to that via the Bios.  Since Feisty release ubuntu sees all drives as '/dev/**s**d?  (it used to be only sata and external drives showed up 'sd?, while ide were 'hd?')

---

