---
title: "No Sound after up grade"
date: 2009-10-30
forum: Installation &amp; Upgrades
---

### Post by stuart221 on 2009-10-30
Hi All
Just up graded to Karmic Koala now I have no sound.

---

### Post by mondo1287 on 2009-10-30
No sound here either.  It worked fine before the upgrade

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

alsamixer: function snd_ctl_open failed for default: No such file or directory

aplay -l
aplay: device_list:223: no soundcards found...

---

### Post by Toadinator on 2009-10-30
First: check if you accidentally hit the mute button.
Second: Unplug then re-plug your speakers in.
Third: Make sure your volume (on Ubuntu; the icon in the corner) isn't at the lowest (I'd try around the middle).

This is what worked for me; might work for you.

---

### Post by mondo1287 on 2009-10-30
> **stuart221 said:**
> Hi All
Just up graded to Karmic Koala now I have no sound.

Stuart, run aplay -l and make sure your sound card is listed.  If you get no sound cards found, you probably have the same issue I do.

---

### Post by skotos on 2009-10-30
FYI
Every audio device of my 4 computers is working fine after upgrading to Karmic, but one of them got muted by the upgrade: _I simply had to clear the mute flag to get sound back._

---

### Post by mondo1287 on 2009-10-30
I got mine working.  The upgrade didn't update /boot/grub/menu.lst  I had to change it to use the latest installed kernel and my sound is back.

---

### Post by mebigfatguy on 2009-10-30
> **mondo1287 said:**
> I got mine working.  The upgrade didn't update /boot/grub/menu.lst  I had to change it to use the latest installed kernel and my sound is back.

Could you please explain this for idiots like me? thanks.

(sound not working as well)

mine is:

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        38ad87a0-e7df-4610-ad59-6e245a54cafd
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=38ad87a0-e7df-4610-ad59-6e245a54cafd ro quiet splash 
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        38ad87a0-e7df-4610-ad59-6e245a54cafd
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=38ad87a0-e7df-4610-ad59-6e245a54cafd ro  single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-15-generic
uuid        38ad87a0-e7df-4610-ad59-6e245a54cafd
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=38ad87a0-e7df-4610-ad59-6e245a54cafd ro quiet splash 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid        38ad87a0-e7df-4610-ad59-6e245a54cafd
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=38ad87a0-e7df-4610-ad59-6e245a54cafd ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, memtest86+
uuid        38ad87a0-e7df-4610-ad59-6e245a54cafd
kernel        /boot/memtest86+.bin
quiet

---

### Post by mondo1287 on 2009-10-30
@mebigfatguy

Your menu.lst is configured properly, as long as default = 0.  Mine was still set to use 2.6.28 and had none of the 2.6.31 entries.  You could delete the 2.6.28 entries to make sure.

Update:  You can fix this automatically by running update-grub
Choose install package maintainer's version if you don't have any custom entries.

---

