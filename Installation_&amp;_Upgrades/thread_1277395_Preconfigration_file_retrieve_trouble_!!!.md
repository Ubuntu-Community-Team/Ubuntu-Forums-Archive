---
title: "Preconfigration file retrieve trouble !!!"
date: 2009-09-28
forum: Installation &amp; Upgrades
---

### Post by nra on 2009-09-28
Hey Guys I am trying to remater ubuntu gutsy iso image.. I have made a preseed file caed Genric.see and out that in "/preseed" directory .. in the isolinux.cfg file, I set the path of the preconfig file to be used as follows :


default unattended

LABEL   unattended
  menu label ^Unattended Installation
  kernel /install/vmlinuz
  append preseed/file=/cdrom/generic.seed debian-installer/locale=en_US netcfg/choose_interface=auto initrd=/install/initrd.gz priority=critical --


I have also tried something like :


default unattended

LABEL   unattended
  menu label ^Cetrea Unattended Installation
  kernel /install/vmlinuz
  append preseed/file=/preseed/generic.seed debian-installer/locale=en_US netcfg/choose_interface=auto initrd=/install/initrd.gz priority=critical --


and generic.see file does exist in /preseed directory before I actually burn it to .iso image .. when I try to do the intstallation it goes fine and then says :

"Failed to retrieve the preconfiguration file"

the file could not be retrived from file:///cdrom/generic.seed 

The installation will proceed in non-automated mode 


can anyone please help me here.. ??

Am I doing something wrong when setting the preseed file from cdrom or /preseed ??


Regards,

Nra
Denmark

---

