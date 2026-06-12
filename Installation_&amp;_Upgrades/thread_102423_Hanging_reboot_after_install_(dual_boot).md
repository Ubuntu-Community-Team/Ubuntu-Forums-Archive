---
title: "Hanging reboot after install (dual boot)"
date: 2005-12-12
forum: Installation &amp; Upgrades
---

### Post by kjericho on 2005-12-12
Hi,

I currently have a 120Gb (IDE1 master) & 40Gb (IDE1 slave) hard disk.  My 120 contains windows xp home and i've decided to install ubuntu onto the 40gb.  So i booted the cd, started the install process and when it came to partitions, i chose "Erase entire disk - hda1 IDE1 slave 40GB" *or similar* and installed it to that.  When that was finished, it had detected XP home and asked to install (multiboot) Grub, i said yes.  When i restarted, it gets to -                                           

[COLOR="Red"]Boot from CD:[/COLOR]  and then does nothing.  I then booted with the XP CD, run the recovery console and ran [COLOR="Red"]fixmbr[/COLOR] after reading some threads. No luck, still hangs at Boot.  Some threads recommend changing the grub file on the hard disk, but im pretty new to using grub so i dont know how to edit it from booting the LiveCD.  Am I doing something wrong? Im not keen to reinstall windows ontop of my current configuration

Thanks,

Karl.

---

### Post by haykel on 2005-12-12
If you have a second drive as slave, I suppose its hdb or hdc (but not hda). You can try this:
- Follow the steps decribed in [LivecdRecovery]("https://wiki.ubuntu.com/LivecdRecovery") replacing hda1 with hdb1 or hdc1
- Then edit /boot/grub/menu.lst and make sure you have the following sections at the end of the file:
```

# Boot windows
title                Microsoft Windows XP
root               (hd0,0)
savedefault
makeactive
chainloader    +1

# Boot Ubuntu
title           Ubuntu, kernel 2.6.12-10-686
root          (hd1,0)
kernel       /boot/vmlinuz-2.6.12-10-686 root=/dev/sda3 ro noapic nolapic quiet splash
initrd        /boot/initrd.img-2.6.12-10-686
savedefault
boot

```

Change **2.6.12-10-686** according to your kernel version (find the files in /boot). Save the file and run:
**grub-install /dev/hda**

Hope this helps!

---

