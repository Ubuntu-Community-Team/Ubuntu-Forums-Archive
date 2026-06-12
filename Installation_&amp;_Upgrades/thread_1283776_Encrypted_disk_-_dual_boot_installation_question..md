---
title: "Encrypted disk - dual boot installation question."
date: 2009-10-05
forum: Installation &amp; Upgrades
---

### Post by Noobie2unbuntu on 2009-10-05
Hello guys (and the occasional girl)!

ok, so I have an AMD64 laptop, currently running WinXP and the entire drive is encrypted (Truecrypt 6.2a) requiring a password before the OS will fire up.

What I'd like to do is install 9.04 from within windows, have Ubuntu's boot loader (GRUB, right?) load AFTER the Truecrypt loader (therefore both OS's are encrypted by the one method).  So after the Truecrypt password has been entered, I can either go into WinXP or U9.04.  Make sense?

Am a little concerned that the installation process will bork the Truecrypt loader and I'll blow the whole Win OS... not quite ready to let that happen. :)

Thanks for the assistance!

---

### Post by Noobie2unbuntu on 2009-10-06
bump...

---

### Post by Noobie2unbuntu on 2009-10-06
Is there no help out there for this issue?

---

### Post by Noobie2unbuntu on 2009-10-07
seriously? anyone?

---

### Post by EJeanmaire on 2009-10-07
If you mess up the Windows loader, worst case scenario you boot of the Truecrypt recovery CD and reload the bootloader.  One thing you will need to make note of is that you will have to install truecrypt on both operating systems, using the bootloader alone wont encrypt both.  There is a trick to using the same encryption keys for both drives, however I do not know/remember the details (look in the truecrypt forums).  Good luck, it will be an adventure to say the least to get this going.

---

