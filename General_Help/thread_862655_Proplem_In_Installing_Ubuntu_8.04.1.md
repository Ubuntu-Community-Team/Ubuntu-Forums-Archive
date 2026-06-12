---
title: "Proplem In Installing Ubuntu 8.04.1"
date: 2008-07-17
forum: General Help
---

### Post by neoncore on 2008-07-17
I Downloaded Ubuntu 8.04.1 Wubi Version x86 version 
ISONAME:ubuntu-8.04.1-desktop-i386
VIrtual Disk SPace Selected: 4GB i tried 5 ALso but FAT Only 4GB MAX
PC SPECS:
CPU:Intel(R) Celeorone(R) 2.66GHZ
786 RAM
Builtin Cards: Intel Vga Card And Builtin Real Take Sound Card
Motherbored:Gigabyte 865G 775 LGA
Windows OS: Windows XP SP2
______________________________________________________________
After Wubi Tell's Me To Reboot i go into ubuntu the logo and load bar comes and then it goes in black screen then comes messages tells Loading,Please Wait..
and the software relese build and if u want support etc.. and about the root and sudo if i want to execute command and nothing else doesn't load or anything i left it like that for 10min without any change please reply

Thanks ,
Neoncore

---

### Post by ago on 2008-07-17
what is the output of

cat /proc/cmdline
cat /proc/mounts
grep err casper.log
grep mount casper.log

---

### Post by neoncore on 2008-07-17
cat proc/cmdline === 
find --set-root --ignore-floppies /ubuntu/install/boot/vmlinuz
kernel /ubuntu/install/boot/vmlinuz debian-installer/custom-installation=/ubuntu/install/custom-installation iso-scan/filename=/ubuntu/install/ubuntu-8.04.1-desktop-i386.iso automatic-ubiquity noprompt quiet splash boot=casper ro debian-installer/locale=en_AU.UTF-8 console-setup/layoutcode=us console-setup/variantcode= --

grep err casper.log == file not found
grep mount casper.log == file not found [same]

Add: i also installed ubuntu 7.04 and it worked well but when i saw the new ubuntu i uninstalled ubuntu 7.04 and downloaded 8.04.1

Also: Is there is way to make logfile for ubuntu when i type commands cuz i had to wr it e lot of things lol

---

### Post by ago on 2008-07-18
There should be casper.log under /
Boot in verbose mode and see what are the last errors you can see

PS even if you create the log, very early on in the boot sequence it would be difficult to copy the log to windows. Or to be more precise, if the windows partition is mounted, then it is a matter of redirecting the output of the commands to a file in there. So if the windows partition is mounted as /root you can do

grep err /casper.log > /root/mylog.txt

If the windows partition is not mounted you have to mount it first, and that may or may not be easy depending on the boot stage you are in. For instance if you installed in a raid, you would not be able to mount it at all.

---

