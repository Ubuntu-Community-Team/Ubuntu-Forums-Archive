---
title: "Installation to 2nd Drive Beeps!"
date: 2009-10-02
forum: Installation &amp; Upgrades
---

### Post by tomBorgia on 2009-10-02
Hiya... I've done plenty Ubuntu installs before so don't think it's anything too stupid I've done wrong!

I've a Hell Optiplex 320 that's been my Windows box for gaming mostly... my Ubuntu Pc is on it's last legs hardware wise so I thought I'd dual boot on the Dell... so I attached another physical disk and ran the install on it... 20GB / partition, 38GB /home and 2GB swap... the device is on Sata channel 3 so the system looks like -

sda1 - Windows / NTFS
sdb - CDROM
sdc1 - Ubuntu / ext3 (/)
sdc2 - Swap
sdc3 - Ubuntu / ext3 (/home)

Everything installed ok and the install CD has been used before... so I reboot it and GRUB comes up ok... with both Ubuntu & Windows on it... so I select Ubuntu and it black screens immediately and the pc beeps... a lot until I switch it off.

I reboot and try the Windows install from GRUB... it loads fine.

So I'm thinking it might be some problem with the disk itself but it was previously working fine... I'm pretty sure it didn't have any jumpers set (primary master / cable select etc) and surely that'd bork the Windows system too and halt at the BIOS.

Any ideas? It's a fresh install so nothing to be lost on reinstall which is my current course of action!

Thanks, Tom.

---

### Post by Bartender on 2009-10-02
Maybe check in the BIOS and make sure that the second HDD shows up in the list of bootable devices?  From my limited experience with them, Dell BIOS'es can have some odd options set at the factory.  I remember one Dell that had all other SATA and PATA channels "disabled" in BIOS.  I had to enable the channel I wanted before it would boot from the added Linux HDD.

---

### Post by tomBorgia on 2009-10-05
Thanks - I had to enable the disk in the bios in the first place... for some reason dell had the sata / pata all disabled... 

After a reinstall got the same problem and noticed some message regarding "drive not ready" (or something like that) before grub loads... and the same kind of thing when booting the livecd... so guess it's a hardware problem... must be something wrong with the hdd.

---

