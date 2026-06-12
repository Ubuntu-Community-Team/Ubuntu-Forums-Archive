---
title: "Acer 5745g DVD Eject button not working"
date: 2010-10-11
forum: Hardware
---

### Post by lhall on 2010-10-11
Hi i just got Ubuntu running on my acer 5745g laptop. Most of it seems to be running fine. But the physical eject button does not work on it. When media is in the drive it will eject from onscreen commands; but with no media i have no way to open the drive now - even with the built in disk utility.

Is there a place to get some drivers for it. It is listed as model name HL-DT-STDVDRAM GT31N.

---

### Post by lhall on 2010-10-11
Well if found typing "eject /dev/sr0" works. But i would like a faster more permanent solution to this. So any input would be great.

This is on 10.10 by the way.

---

### Post by borikru on 2010-10-23
I have the same problem with Acer Aspire 5745G on 10.10 64 bit.

The button works during boot, but as soon as login screen appears it stops ejecting the drive.

---

### Post by borikru on 2010-10-24
Fixed by upgrading BIOS to 1.16.

1) Boot to Windows (I had it installed on a portable USB drive),
2) Download latest BIOS fro Acer 
3) Burn the new BIOS
4) Reboot to Ubuntu and the eject button should be functional now

---

