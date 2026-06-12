---
title: "Possible to reinstall dual-boot without messing up bootloader?"
date: 2009-06-16
forum: Installation &amp; Upgrades
---

### Post by ZachMitchell on 2009-06-16
I believe I need to reinstall Ubuntu with my SATA drives enabled in a different mode. I triple boot Ubuntu with Windows XP and Windows Vista. As most of you know installing Ubuntu over an already dual-booted system between XP and Vista allows you to choose the Vista boot loader in the GRUB menu. I just want to make sure reinstalling Ubuntu won't cause me to loose my windows bootloader and not be able to boot into Windows anymore. I know I can do the repair thing in windows but it's a hell of a process getting it all fixed..when I could rather avoid it. Any ideas?

---

### Post by Mark Phelps on 2009-06-16
You can certainly install Ubuntu and not install GRUB, but then, you will have to use a windows-based loader to launch Ubuntu, something like EasyBCD with NeoGRUB (from NeoSmart).

---

### Post by ZachMitchell on 2009-06-16
That's a thought to keep, however I'd like to use GRUB if possible. Is it possible to keep my current GRUB configuration with a clean install of Ubuntu?

---

### Post by Mark Phelps on 2009-06-16
> **ZachMitchell said:**
> That's a thought to keep, however I'd like to use GRUB if possible. Is it possible to keep my current GRUB configuration with a clean install of Ubuntu?

Unless you created a specific boot partition just to hold GRUB, you most probably installed GRUB to the MBR and to your first Linux partition.  If you save off the current menu.lst file, you will be able to restore that after you reinstall Ubuntu and GRUB, and will get your settings back.

If you just reinstall Ubuntu over itself and don't reformat the partition(s), the /boot directory should be OK with all the GRUB stuff still in it.

If you also reinstall GRUB, it will overwrite the MBR, but if your saved menu.lst file has the stanzas for launching MS Windows, you just copy that back, reboot, and you'll be good to go.

---

### Post by ZachMitchell on 2009-06-16
Wouldn't doing a clean install look at my other operating systems the same way it did the first time and automatically add them to GRUB? (Just saying by logic I don't see why not) I really just want to be sure before I do this.

---

