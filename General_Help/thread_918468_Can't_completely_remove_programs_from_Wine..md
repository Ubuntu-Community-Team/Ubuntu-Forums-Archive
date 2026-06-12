---
title: "Can't completely remove programs from Wine."
date: 2008-09-12
forum: General Help
---

### Post by kokkus on 2008-09-12
HI. I have some problems with WIne.
I tried to uninstall the program but it won't go away from the list. 
Not even the uninstallation program will escape.
I deleted the programs folder (/itunes)
Deleted it from the programs menu list by using 
nautilus ~/.local/share/applications/wine
But I can't completely remove it like as it hasn't been on my PC at all.

Please help me with this. THaks in advance :)

---

### Post by quibbler on 2008-09-13
> **kokkus said:**
> HI. I have some problems with WIne.
I tried to uninstall the program but it won't go away from the list. 
Not even the uninstallation program will escape.
I deleted the programs folder (/itunes)
Deleted it from the programs menu list by using 
nautilus ~/.local/share/applications/wine
But I can't completely remove it like as it hasn't been on my PC at all.

Please help me with this. THaks in advance :)
Go to /home/your_name/.config/menus/applications-merged
and delete the itunes there. It should now be gone in the menu.

Regards quibbler

---

### Post by kokkus on 2008-09-13
Thanks. That was the menu but what about the uninstallation list for wine. That's what I ment. I will completely remove programs from wine.

---

### Post by mb_webguy on 2008-09-13
Go to "~/.wine/drive_c/Program Files/" and delete the folder for the program, then go to Wine's Uninstall Software and try to remove it.  When Wine isn't able to find the program to uninstall, it should ask you if you want to remove the entry from the list.

---

### Post by kokkus on 2008-09-15
Thank you, but that's what I am trying to explain. Wine won't delete the uninstallation link anyway. I deleted the program filder, installsheld installation program and everything related to the program, and it still won't go away from the list.

---

### Post by outdoorsman14 on 2008-09-24
In order to remove the program from the list you need to switch to the directory that was mentioned earlier. Type this into a terminal:

 cd /home/your_name/.config/menus/applications-merged

when you get to this directory type:

ls

This will give a list of available files in that directory. Find the file that corresponds to QuickTime and type this:

rm wine-Programs-QuickTime.menu

I believe that was the file for that.

If it is still there and is just listed on the wine menu extension, like I had found Apple Update to be, you are going to have to go into the wine-Programs.menu and edit it. Try this:

gedit wine-Programs.menu

find the line that says what the file is and then put a # next to it, as well as the <include> after it. This should remove whatever you need :)

---

