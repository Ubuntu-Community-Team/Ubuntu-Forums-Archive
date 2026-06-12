---
title: "Cant install GRUB(or LILO)"
date: 2006-02-17
forum: Installation &amp; Upgrades
---

### Post by reidms on 2006-02-17
I go through the installation procces for Kubuntu fone, but I cant install GRUB or LILO.  I have even tried installing grub to a floppy(fd0).

I am installing linux on my slave HD, and windows xp is on my primary hd.
My drives are NTFS.

I have checked the disk's integrity.

---

### Post by shams2 on 2006-02-17
what to do you mean by can't install? where did you select to install the grub to the mbr or root partition? any error message while installation? if you mean you can't boot after installaton complete please post the /boot/grub/menu.lst using any live  cd and the slave hard disk map, and tell us which hard disk is the primpary at bios?

---

### Post by reidms on 2006-02-19
grub wont install anywhere.  Not on the MBR nor a floppy or anything else.

---

### Post by reidms on 2006-02-20
Also, I do not have an error # from grub, because I cant even install it.  It just says grub could not be installed.

---

### Post by devil_dobie on 2006-02-20
I get LILO error # 1 when trying to install it to the MBR.  I am sorry that I am not helping you in the situation, just letting you know that I am out here looking for the same answer.

I figured that it was related to the BIOS not allowing anything to be written to the MBR.  Went back and sure enough it was sent to deny (I changed it to "allow").  Now I have everything installed, but can't boot into it.  When I put the install disk in to boot into Linux, and run liloconfig, the command is not recognized anymore.

---

### Post by reidms on 2006-02-20
Hey, thanks- I will try to go into the bios and allow writing to the MBR
Ill post a follow up-

---

