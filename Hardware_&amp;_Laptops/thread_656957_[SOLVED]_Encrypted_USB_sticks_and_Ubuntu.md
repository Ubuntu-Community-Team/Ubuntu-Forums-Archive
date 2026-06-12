---
title: "[SOLVED] Encrypted USB sticks and Ubuntu?"
date: 2008-01-03
forum: Hardware &amp; Laptops
---

### Post by jazzgossen on 2008-01-03
I want to install Ubuntu on a high-speed USB flash stick. However, it seems that all sufficiently large (>= 4 GB) and sufficiently fast (>= 30 MB/s read speed) have some encryption "feature" that (according to specs, at least) is only compatible with Windows.

Do you know if it's possible to delete the encrypted vault on, for example, the Corsair Flash Voyager GT? By just reformatting the stick to an ext2 file system, maybe?

If not, do you know if it's possible to use the encypted partition (Corsair says that it uses TrueCrypt but only compatible with Windows) with Ubuntu?

Or do you know of another large and fast USB flash stick that just works as normal?

---

### Post by fiddledd on 2008-01-03
The 4gb Corsair Flash Voyager I have didn't have an encrypted partition on it, just Truecrypt setup program for Windows. I just formated it using Gparted anyway. BTW Truecrypt is available for Ubuntu and also Easycrypt which is a frontend for it.

---

### Post by jazzgossen on 2008-01-10
OK. The encryption was no problem (I think). But I can't boot from the Corsair Flash Voyager.

I have previously installed Ubuntu 7.10 to an OCZ Rally 1 GB stick, which worked well apart from the lack of space. After doing the same thing with the Corsair stick, the computer says "Can't load operating system" when I reboot. Trying to run grub-install on the stick, grub says something about "input/output error" and that it doesn't recognize the file system. However, I can mount the stick and all the installed files are there.

Any ideas?

---

### Post by jazzgossen on 2008-01-18
Turns out the booting problem was mainly a BIOS issue. After reloading failsafe defaults and re-enabling only enough to get the USB controller working, the stick boots.

---

