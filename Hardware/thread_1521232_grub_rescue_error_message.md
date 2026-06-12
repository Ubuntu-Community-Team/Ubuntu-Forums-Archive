---
title: "grub rescue error message"
date: 2010-06-30
forum: Hardware
---

### Post by HooDzy on 2010-06-30
error: no such device: 3e6d8285-27df-445d-8c37-29fdc9662bfe.
grub rescue>_

this is the exact error i get as i start my computer up. I recently received an external hard drive from school and put ubuntu on it. Every time i started up my comp without the hard dirve connected to the comp i received this message, i cleared the external and now i cannot use my computer at all i think it has something to do with a driver i changed but im not positive any help would be awesome thanks!!!!!!!

edit: all i want to do is use windows again on my laptop

---

### Post by Yellow Pasque on 2010-06-30
What kind of laptop do you have (a dell of some sort I see from your cross-posting) and did you get a windows recovery cd?

---

### Post by HooDzy on 2010-06-30
dell studio 1535 and i dont have the recovery cd ive had the computer for a few years i must of misplaced it (sorry about the cross-post i meant to delete 1)

---

### Post by Yellow Pasque on 2010-06-30
Use method 2:
[http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7](http://ubuntuguide.net/how-to-restore-grub-2-after-reinstalling-windows-xpvistawin7)

---

### Post by bcbc on 2010-06-30
You need to get the windows bootloader back on your internal drive.

Boot from the install cd you used to install ubuntu, select 'try without any changes'.

Then go to a command line (ignore warnings after first command, they're normal):
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

This puts a windows-equivalent bootloader on your internal drive. 

If you have a windows repair cd you could use it instead to repair the bootloader: run "fixmbr" (for XP) or "bootrec.exe" /fixmbr (vista/7)


EDIT: background: when you install ubuntu to an external it defaults to install the grub2 bootloader to /dev/sda (internal harddrive). This means that when you boot, the bios looks in the internal drive MBR and grub2 then looks for the external to load the grub menu. If you unplug the external, grub2 can't find it and you see the error you got.
Normally, if you do this again, when you install ubuntu select advanced (when installing the bootloader) and install grub2 only to the external drive (/dev/sdb). Then when the external is plugged in, boot from it (override boot device at startup). When the external is not plugged in, you just boot normally into windows.

---

