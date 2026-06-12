---
title: "Need help installing 3rd OS"
date: 2008-12-21
forum: Installation &amp; Upgrades
---

### Post by clay7 on 2008-12-21
Hello,

I have a box with 2 SATA drives. On the primary is Windows XP only. On the second SATA is Ubuntu 8.10 only. Both have tons of space available.

I would like to install Fedora on the same drive as Ubuntu. Will Fedora mess up my MBR? What advice would you give me?

Thanks!

---

### Post by tad1073 on 2008-12-21
It messed up my install. Fedora uses a different kind of boot loader which didn't pick-up my other OS's.

---

### Post by SuperSonic4 on 2008-12-21
> **tad1073 said:**
> It messed up my install. Fedora uses a different kind of boot loader which didn't pick-up my other OS's.

+1 fedora broke and I had to use mandriva to get it's bootloader back

---

### Post by logos34 on 2008-12-21
I would advise you not to make a separate /boot (which I think is the Fedora default action).  When you get to the Grub installation section, tell it to write the bootloader to the Fedora / partition ('/dev/sd??), not the MBR.  Then just add a 'configfile' or 'chainloader' entry for Fedora to your ubuntu Grub menu.lst [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#1._Configfile").

---

### Post by clay7 on 2008-12-21
Hmmm...doesn't look as easy as the Ubuntu install (which was flawless). I'll study up on the GRUB page, and if I think I can pull it off, I'll give it a go.

Thanks for your inputs!

---

### Post by markbuntu on 2008-12-21
If you install the bootloader for fedora in the same partition as you install fedora you can just add a chainloader in the ubuntu /boot/grub/menu.lst for fedora and you should be OK.

```

#    Fedora
root   (hd1,1)
makeactive
chanloader +1

```

just make sure you have the partition right. This will hand off the boot to the fedora bootloader and get out of the way. This will avoid any problems with kernel updates etc. I have 4 OSs on 4 drives on my machine and chainload 3 of them from the grub on hd0. 

grub uses hda for drive designations. If you have sda drives they are mapped in /boot/grub/device.map

I keep a few backups of that menu.lst and device.map just in case....

---

