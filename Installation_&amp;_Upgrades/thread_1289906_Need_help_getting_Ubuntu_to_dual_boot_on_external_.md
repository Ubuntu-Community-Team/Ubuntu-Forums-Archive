---
title: "Need help getting Ubuntu to dual boot on external HDD"
date: 2009-10-12
forum: Installation &amp; Upgrades
---

### Post by inuyasha10121 on 2009-10-12
Hello everyone, its time for the noob of the day to ask a question. I'm trying to get Ubuntu 9.04 to boot on an external HDD that I have on my Dell Studio XPS. I've got it installed properly, but the problem is, grub is my default bootloader. This means that I have to have my external HDD plugged in to boot, which is not acceptable. I have EasyBCD loaded on Vista side, and I can still get to the vista side. What I need to know is how o set up EasyBCD(NeoGRUB or the standard linux adder, which ever is easier) to dual boot with Vista as the normal boot sector, not the external. Ask for any information needed, and it will be supplied(I don' know what you guys need to diagnose this, but I can povide it)
Thanks for reading, and I hope someone can help out ^^

---

### Post by Bartender on 2009-10-13
This doesn't address EasyBCD but similar situation

[http://ubuntuforums.org/showthread.php?t=1289551](http://ubuntuforums.org/showthread.php?t=1289551)

---

### Post by presence1960 on 2009-10-13
> **inuyasha10121 said:**
> Hello everyone, its time for the noob of the day to ask a question. I'm trying to get Ubuntu 9.04 to boot on an external HDD that I have on my Dell Studio XPS. I've got it installed properly, but the problem is, grub is my default bootloader. This means that I have to have my external HDD plugged in to boot, which is not acceptable. I have EasyBCD loaded on Vista side, and I can still get to the vista side. What I need to know is how o set up EasyBCD(NeoGRUB or the standard linux adder, which ever is easier) to dual boot with Vista as the normal boot sector, not the external. Ask for any information needed, and it will be supplied(I don' know what you guys need to diagnose this, but I can povide it)
Thanks for reading, and I hope someone can help out ^^

I don't know about EasyBCD. Uninstall EasyBCD it is not needed. If you put GRUB on MBR of the external disk & restore Windows to MBR of the internal disk you can do this provided your machine is capable of booting from USB or Removable media:

After doing the above reboot & go into BIOS and set your external disk to boot before your internal disk. Save changes to CMOS and exit BIOS. Now when you boot without the external plugged in you will boot right into windows. When you boot with the external plugged in you will get GRUB and can boot into Ubuntu.

You can do this without EasyBCD. If you need specific instructions on how to do this post back.

---

