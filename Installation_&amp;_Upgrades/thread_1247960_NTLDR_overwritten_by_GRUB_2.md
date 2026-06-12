---
title: "NTLDR overwritten by GRUB 2"
date: 2009-08-23
forum: Installation &amp; Upgrades
---

### Post by fela on 2009-08-23
I installed Ubuntu karmic koala (with grub 2) to the extra partition on my harddrive. Normally when installing ubuntu with GRUB legacy, it keeps the ntldr windows bootloader. Not so in this case: now when I boot windows, it boots but with GRUB4DOS, instead of NTLDR. I would like to use NTLDR because there's an option that I want to use with it (noguiboot). Strange thing is, there doesn't seem to be a trace of NTLDR anywhere on my windows partition. Do you think that there's any chance of restoring ntldr to my windows partition? I also have another drive with intrepid on it (grub legacy) - grub legacy is installed to the MBR of my main (windows and karmic) drive with the boot files such as menu.lst on my intrepid drive.

thanks :)

---

### Post by VMC on 2009-08-23
grub4dos has nothing to due with grub2. Different boot managers. What do you mean boot from NTLDR. Do you want Windows boot manager? Grub2 can boot both Windows and Linux.

---

### Post by fela on 2009-08-23
> **VMC said:**
> grub4dos has nothing to due with grub2. Different boot managers. What do you mean boot from NTLDR. Do you want Windows boot manager? Grub2 can boot both Windows and Linux.

Well before when grub2 wasn't involved, I was chainloading the NTLDR from grub legacy, and it seemed to work fine. That's what I want now, but NTLDR doesn't seem to have been installed correctly, or was overwritten. It might be nothing to do with grub2 I guess.

---

