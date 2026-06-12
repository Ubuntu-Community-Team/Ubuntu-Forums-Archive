---
title: "Grub Config"
date: 2005-12-19
forum: Installation &amp; Upgrades
---

### Post by DoorGunner on 2005-12-19
Hi

I recently installed Ubuntu 5.10 on my machine. I did not load grub. However, I am using Fedora Cores Grub instead. I read another article for ubuntu's grub config and stated this.

title		Ubuntu, kernel 2.6.10-5-686 
root		(hd0,2)
kernel		/vmlinuz-2.6.10-5-686 root=/dev/hda6 ro quiet splash
initrd		/initrd.img-2.6.10-5-686
savedefault
boot

However, The article was dated back in october sometime so i am not sure if it is currently valid.

I am wondering what is the current grub config for a fresh ubuntu install?

---

### Post by matthew on 2005-12-19
This is what I had. You probably one need the first entry. Remember to update te fedora grub when you install a new kernel in Ubuntu (that last sentence probably wasn't necessary, but just in case someone new to the Linux world is reading this...).

```
title        Ubuntu, kernel 2.6.12-9-386 
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd        /boot/initrd.img-2.6.12-9-386
savedefault
boot

title        Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root        (hd0,1)
kernel        /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd        /boot/initrd.img-2.6.12-9-386
boot

title        Ubuntu, memtest86+
root        (hd0,1)
kernel        /boot/memtest86+.bin  
boot
```

---

### Post by DoorGunner on 2005-12-19
Thank you very much

Works great....I am using ubuntu as I type.....:) 

This is resolved

---

### Post by matthew on 2005-12-19
[quote=DoorGunner]Thank you very much

Works great....I am using ubuntu as I type.....:) 

This is resolved[/quote]Cool. Glad I could help. Have fun!

---

