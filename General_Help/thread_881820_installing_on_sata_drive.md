---
title: "installing on sata drive"
date: 2008-08-06
forum: General Help
---

### Post by stav on 2008-08-06
hi, I am very new to Ubuntu so please bare with me! :)

I have just installed and setup a server with it so i can access all of my harddrives from my mac machines. I turned it off last night and then it wouldnt boot this morning. I have decided anyway to reinstall it on my raptor drive but with no hope.

I am using an old abit nf7-s board which has sata ports but is not detecting my harddrive to partition it ??? I know from windows you would put in a floppy disk and load the drivers but how would I get round this problem and help ubuntu see my hard drive . . . . 

Thanks in advance to a very confused person!!!

Stav

---

### Post by tamoneya on 2008-08-06
go into the bios and change the sata mode from ACHI to ide or compatibility.

---

### Post by Krupski on 2008-08-06
> **tamoneya said:**
> go into the bios and change the sata mode from ACHI to ide or compatibility.

I wonder if the OP isn't having the "magical random drive designation" problem?

Ubuntu has built in support for AHCI... I don't need any special driver disk when installing it (although I DO if I use XP - which doesn't have AHCI built in).

Sometimes I install Ubuntu onto a USB hard drive as an "expendable" experimental setup.

The drive is initally setup (i.e. GRUB) as HD3,0 but upon reboot I have to edit that line to say HD0,0 or else it won't boot.

Once I boot, I have to edit /boot/grub/menu.lst and fix the HD number so that it will boot in the future (without having to mess with the start screen).

-- Roger

---

