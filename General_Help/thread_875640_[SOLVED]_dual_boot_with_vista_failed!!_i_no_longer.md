---
title: "[SOLVED] dual boot with vista failed!! i no longer have acess to ubuntu"
date: 2008-07-31
forum: General Help
---

### Post by cowboyup6983 on 2008-07-31
okay so i am stuck, i was trying to install vista as a backup with 80GB of hard drive space, i was using this site to help me. 
[http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm](http://apcmag.com/how_to_dualboot_vista_with_linux_linux_is_already_installed.htm)

i got to page five after installing vista and then i downloaded  EasyBCD by Neosmart. i followed these directions:

To enable access to the Linux partition, the best option is to install NeoGrub. Go to "Add/Remove Entries", go the NeoGrub tab and select "Install NeoGrub". This adds the "NeoGrub Bootloader" option to the Vista bootloader. 

Once that's done, choose Configure - this launches the NeoGrub menu.lst file, location at C:\NST\menu.lst. Use Notepad or Wordpad to open the file, and then paste in the boot entries from the backup copy of MENU.LST you made earlier. These entries occur between "## ## End Default Options ##" and "### END DEBIAN AUTOMATIC KERNELS LIST". Save and exit, then reboot the machine. 

i open the file that i saved from ubuntu "GRUB boot menu" and save paste in the boot entries and save file to the same location and reboot.

once i reboot i do get vista bootloader and NeoGrub Bootloader but when i choose neogrub and this list of ubuntu comes up when i choose one i get an instant error 17-file not found. 

so i can only boot into vista and i dont want to boot to vista, just wanted it as a backup if ever needed. im stuck can someone please help me get back into ubuntu

---

### Post by zvacet on 2008-07-31
Try to [reinstall grub.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

---

### Post by cowboyup6983 on 2008-07-31
> **zvacet said:**
> Try to [reinstall grub.]("http://ubuntuforums.org/showthread.php?t=224351&highlight=reinstall+grub")

well i was so mad, i eneded up reinstalling vista on a 400GB hard drive and after that was complete, i install ubuntu 8.04 on a 500GB hard drive and im now going through the updates and reinstall everything like before. 

i was having problems with ubuntu x64 bit anyway, this time i installed 32 bit. does anyone know whats the max RAM ubuntu x32 will show.

---

### Post by bodhi.zazen on 2008-07-31
Depends on your processor. With PAE you can get up to 64 Gb.

[http://ubuntuforums.org/showthread.php?t=855511](http://ubuntuforums.org/showthread.php?t=855511)

---

