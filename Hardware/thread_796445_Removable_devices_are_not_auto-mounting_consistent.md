---
title: "Removable devices are not auto-mounting consistently"
date: 2008-05-16
forum: Hardware
---

### Post by deadtom on 2008-05-16
I'm noticing this with CDs and MMC/SD cards. Sometimes when I pop one in the window pops up asking what to do and sometimes nothing at all. In this case they show up in dmesg just fine with no errors and I can mount them manually but would like to not have to mess with that.

---

### Post by deadtom on 2008-05-26
-bump-


Still having the same issue.

---

### Post by prshah on 2008-05-29
> **deadtom said:**
> I'm noticing this with CDs and MMC/SD cards. Sometimes when I pop one in the window pops up asking what to do and sometimes nothing at all. In this case they show up in dmesg just fine with no errors and I can mount them manually but would like to not have to mess with that.

Are you "unmounting" them before removing them? 

Also, I have disabled icons on the desktop (through gconf-editor) and I find that CDs no longer mount by just clicking them on the "places" menu; I have to go through Places-Computer. Have you also disabled desktop icons (scrabbling for straws).

---

### Post by deadtom on 2008-05-29
Yes, I always unmount before removing devices.

No, I have not disabled desktop icons. I'm using kde rather than gnome and what used to happen was I'd put in a cd or sdcard or usb drive and a window would pop up asking me what I want to do with it just like what happens in ms windows. This no longer happens. Nothing happens at all.

I've made some entries in fstab and I use kdf now to mount and unmount things but it would be nice to get that pop up window back. I'm sure it was some program that I don't know the name of that either i've broken or accidentally uninstalled. I've been through adept very carefully and cannot figure out which app did this for me.

---

