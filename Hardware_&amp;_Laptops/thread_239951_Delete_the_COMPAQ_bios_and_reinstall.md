---
title: "Delete the COMPAQ bios and reinstall"
date: 2006-08-20
forum: Hardware &amp; Laptops
---

### Post by CameronCalver on 2006-08-20
Hello i have an old compaq computer which i would like to install ubuntu on but i cannot becuase it will not let me boot from cd so i donwloaded that boot manager but it  cant find the cdrom at start up.
There is no normal bios on this machine all it is is a big
[SIZE="5"]COMPAQ[/SIZE] logo then it boots win 98 (which i deleted) and becuase it boots only the floppy drive i would like to download a new bios software and install it from the floppy but i am unsure of this even being possible

---

### Post by matko on 2006-08-20
> **CameronCalver said:**
> Hello i have an old compaq computer which i would like to install ubuntu on but i cannot becuase it will not let me boot from cd so i donwloaded that boot manager but it  cant find the cdrom at start up.
There is no normal bios on this machine all it is is a big
[SIZE="5"]COMPAQ[/SIZE] logo then it boots win 98 (which i deleted) and becuase it boots only the floppy drive i would like to download a new bios software and install it from the floppy but i am unsure of this even being possible

sure it is possible. you can flash your bios. but it is highly recommend you go compaq site and download bios **exactly** for your pc (MB). You should found on compaq site *.bin file (bio) and special flash utility made by and only for compaq.

be carefull with flashing bios

---

### Post by LKRaider on 2006-08-20
During the display of the big COMPAQ logo, try pressing "Delete" several times. If that doesnt work try with "F1", "F2" and also "F10" (these are the default keys on some pc's) and it should go into the bios setup.

Inside the bios setup, search for the "boot order" option, and see if you can configure it to boot from the cd drive.

Also, be sure to disable the option to show the logo during boot too. (sometimes called quiet boot, silent boot, quick boot, boot diagnostics, show post messages, or whatever).


PS: if it is a Compaq Deskpro 4000 the process to get into the BIOS is more complex (requires special boot disks) and just pressing the keys won't work.

---

