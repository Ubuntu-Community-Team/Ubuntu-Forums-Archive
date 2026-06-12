---
title: "ubuntu and window on the same partition"
date: 2008-10-06
forum: General Help
---

### Post by linhdkl on 2008-10-06
hi !

My problem is:

in my computer has only one partition, it is C: (80G)
in this partition i used for window xp sp2, and now i install ubuntu 8.x (on window - Wubi-8.04.1-rev506.exe)
it ok !

-> Restart computer..
-> Choose: window xp/ Ubuntu (select ubuntu -> OK)
-> Ubuntu Install .... 
           and it stoped when formatting swap space... 

some body help me to resolve this problem but not to divided partition ?

Thanks for your help !

---

### Post by paulhart on 2008-10-06
I have a 74GB Raptor drive, running Win32XPPro just fine. I down loaded the ISO file from UbuntuStudio for 64bit, ('cause I wanted to run 64bit Linux, but it could have been the 32bit just as easy), burned the file to a CD, then booted to the CD and followed the directions to have it correctly setup a small partition for UbuntuStudio, a Swap, and the original WinXP in it place. It then dual boots, and I pick UbuntuStudio or WinXP, without problem. It handled the whole process and installed a nice collection of "artist friendly" software tools that are accessible from the menus. I have an extra drive which I used for backing up everything beforehand, just in case, always a good idea. Now I use the same drive to have a backup of the complete OS, Win and Linux, using Acronis from the Win32 side. Saved my "butt" on several occasions. I use the Linux build to run 64bit apps solid, such as Blender for big projects. 
Good luck with the effort. Partitioning is a fine way to go, especially when the CD "holds your hand" and does the work.
Paul

---

### Post by Sef on 2008-10-06
1) The only way to install without partitioning is to use wubi - otherwise partitioning is necessary.   

2) How much space do you have left on the disk?

3) Did you defrag windows 2 or 3 times before installing wubi?

4) Moved to wubi forums.

---

### Post by ago on 2008-10-06
If wubi canno format the swap space this means that your disk is extremely fragmented. Uninstall wubi, run jkdefrag or similar to defragment the disk, then install again

---

