---
title: "install ubuntu onto laptop w/2 harddrives without grub"
date: 2009-08-28
forum: Installation &amp; Upgrades
---

### Post by total0wnage on 2009-08-28
hey guys im trying to install ubuntu onto my laptop which contains 2 harddrives but without using grub. i have no option in my boot menu to choose which harddrive it just says Notebook harddrive so i was wondering if there was a way to choose the 2nd harddrive so that ubuntu wil boot.

---

### Post by running_rabbit07 on 2009-08-28
> **total0wnage said:**
> hey guys im trying to install ubuntu onto my laptop which contains 2 harddrives but without using grub. i have no option in my boot menu to choose which harddrive it just says Notebook harddrive so i was wondering if there was a way to choose the 2nd harddrive so that ubuntu wil boot.

No grub, no boot. Same as Windows has to have the bootstrap loader.

---

### Post by stlsaint on 2009-08-28
have you checked to see if bios will allow the change. you should be able to boot to the external drive if thats the one with Grub...apptop can you boot to live cd and see ext hdd mounted?

---

### Post by total0wnage on 2009-08-28
well isnt there a way to modify the windows bootloader and add a line to add linux to the list

---

### Post by running_rabbit07 on 2009-08-28
> **total0wnage said:**
> well isnt there a way to modify the windows bootloader and add a line to add linux to the list
That is what grub does.

---

### Post by total0wnage on 2009-08-28
well last tiem i installed grub i got screwd because i wasnt able to get get into safe mode and something else i dont remeber but it was a big problem and i had to send my laptop out to HP because i couldnt get into windows either

---

### Post by running_rabbit07 on 2009-08-28
It is easy to set the grub menu to show the restore options once installed. If you want I will put together a quick screenshot show to show you how.

These shots are on the 8.04 machine but the menus and process are the same.

---

### Post by total0wnage on 2009-08-28
thank you, do i have to format my 2nd harddrive and reinstall ubuntu or is there a way i can install grub with ubuntu already installed

---

### Post by stlsaint on 2009-08-28
yes you can install Grub without formatting...i would tell you but it would be better to give you resources to learn from...see signature for MBR/GRUB or GRUB

---

### Post by running_rabbit07 on 2009-08-28
This[ thread]("http://ubuntuforums.org/showthread.php?t=224351") will show you how to install grub via the LiveCD without reinstalling Ubuntu. Or, click the Grub link in stlsaint's signature.

---

### Post by running_rabbit07 on 2009-08-29
One thing I just noticed while using an alternate install ISO is that it has an option for restoring a broken system. If it will make you fell more comfortable you can burn the alternate installer to disk and store it for just in case purposes.

---

