---
title: "boot ubuntu from external hdd"
date: 2006-10-25
forum: Hardware &amp; Laptops
---

### Post by zmat on 2006-10-25
hi,

I need help installing ubuntu on an external hdd. Basically i want to "isolate" ubuntu on the external hdd. The way my bios works if the external usb hdd is not turned on at bootup, it will boot direct from laptop hdd, but if it is turned on, it'll boot from external hdd instead.

So what i am going to do, is partition the external hdd, one ext3 as ubuntu and the other as ntfs to backup all my windows based stuff- movies, music watever. When i want to boot ubuntu i'll just turn on external hdd at bootup, but when i want to boot windows (from my laptop hdd) i'll leave the external hdd off at bootup, and i want windows to start straight away--without grub i.e. i don't want grub to install onto laptop hdd mbr. So basically i "isolate" ubuntu so that if i decide i don't like it i can just delete the partition and thats it.

Will this work? I assume i need to install grub onto the external hdd MBR, or the ubuntu ext3 partition...because i obviously don't want it to touch the laptop hdd. Will ubuntu setup allow me to do this, and are there are issues with this setup?

---

### Post by hikaricore on 2006-10-26
I'm too tired to go into great detail with this, but I had a quick thought on it.  Ubuntu installs grub on the boot drive of your system by defualt (i believe). Assuming you computer will boot from either device, you could disconnect your internal hard drive while installing ubuntu leaving only your external drive connected.  And just install to your external HD from the cd.  It won't matter what the install does as far as grub because it will only affect your external driver, as the internal will be disconnected.  :)  Simplicity is probably the easiest way to go.  Not saying you should rip your laptop apart to disconnect the HD, but if it's like most I've personally dealt with, this won't be an insanely complex task.

Good luck.

---

### Post by hearnden on 2006-10-26
I'm pretty sure you can do this.  I had to install ubuntu on my desktop hdd using my laptop and an hd enclosure, because ubuntu can't use my desktop cd-rom.  I remember being pleasantly surprised that the installer was able to do it relatively painlessly, but I can't remember many details sorry.

---

