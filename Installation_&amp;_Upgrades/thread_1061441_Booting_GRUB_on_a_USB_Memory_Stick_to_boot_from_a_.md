---
title: "Booting GRUB on a USB Memory Stick to boot from a CDROM"
date: 2009-02-05
forum: Installation &amp; Upgrades
---

### Post by NDemar on 2009-02-05
Ok, this sounds strange, but I have a very odd issue. 

I need to rebuild a few systems that have a bios 'security' fix that do not offer booting from a CDROM, but I can boot from GRUB on a USB Memory stick. I have verified the CDROM is visible as a device (USBLinux works and sees the drive)

Is it possible for me to configure Grub to have a menu Item to redirect a boot to a CDROM?

---

### Post by caljohnsmith on 2009-02-05
I would recommend trying the PLoP Boot Manager, because it can usually boot a CD-ROM. And you don't even have to give up Grub to try it, you can boot PLoP from your Grub menu. If you want to give it a try, how about downloading the [plpbt-5.0.zip]("http://download.plop.at/files/bootmngr/plpbt-5.0.zip") file to your desktop and do:
```
cd ~/Desktop
unzip plp*.zip
sudo cp plp*/plpbt.bin /boot
```
Then add PLoP to the Grub menu with:
```
title PLoP
root [COLOR="Blue"](hdX,Y)[/COLOR]
kernel /boot/plpbt.bin
```
And of course change (hdX,Y) to be whichever partition you are in since that will have PLoP in the /boot directory. Let me know how that goes or if you run into problems.

---

### Post by lha on 2009-02-07
> **NDemar said:**
> Is it possible for me to configure Grub to have a menu Item to redirect a boot to a CDROM?

You can chainload Smart Bootmanager and use it to boot a cd. For instructions, see [http://www.gentoo-wiki.info/GRUB/Chainloaded_CD-ROM]("http://www.gentoo-wiki.info/GRUB/Chainloaded_CD-ROM") and [http://www.lrz-muenchen.de/~bernhard/grub-chain-cd.html]("http://www.lrz-muenchen.de/~bernhard/grub-chain-cd.html").

---

