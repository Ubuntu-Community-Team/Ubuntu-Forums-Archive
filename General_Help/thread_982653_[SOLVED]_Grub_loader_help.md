---
title: "[SOLVED] Grub loader help"
date: 2008-11-14
forum: General Help
---

### Post by banana jama on 2008-11-14
I've been using ubuntu for about 2 weeks now and got all my bug straighten out (through the  forum's help of course) i like ubuntu so much and use microsoft so little i decided to delete the microsoft partion from my computer now it's 100% UBUNTU!!!! :) 
 one problem through when i turn on my computer the grub starts up and the microsoft option is still there as a option to run. how to i delete the microsoft (long head loader) from grub. im using ubuntu 8.10 and i think the grub version is 1.5 or whatever the newest version is.

---

### Post by WWSmith36 on 2008-11-14
Open a terminal from menu Applications-> Accessories-> Terminal and type

gksudo gedit /boot/grub/menu.lst

Scroll down to the end of the file and delete your windows entry

Save and Close

---

### Post by thestig_992 on 2008-11-14
grub uses a file in /boot/grub/menu.lst to list OSs in its menu.

make a backup copy of the menu.lst file (sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bkp)

Then open the original file with root permissions (sudo gedit /boot/grub/menu.lst)

Scroll to the bottom, and delete the lines with windows. There will be about 4 or 5 lines to delete, all clumped together...

Be careful using sudo, as it will give you acess to do anything to your drive

---

### Post by Killtodie on 2008-11-14
also change the load time to 0 seconds so you dont see it

---

### Post by thestig_992 on 2008-11-14
haha 3 posts at the same time

epic win

---

### Post by banana jama on 2008-11-16
thanks it work. o yea thanks for the suggestion about the load time being 0 now i can just get straight ubuntu now.

---

