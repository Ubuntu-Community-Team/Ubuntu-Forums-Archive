---
title: "Managed to delete ubuntu from windows"
date: 2008-10-11
forum: General Help
---

### Post by zslastman on 2008-10-11
I'm dual booting windows xp and ubuntu on my laptop. Xp was running very slowly so i decided to clean out some disk space on it. I put in a search for "ubuntu" and deleted everything that came up, the idea being to delete my iso file etc that i used to install it, since as far as i knew, Ubuntu itself was invisible to windows, and couldn't be deleted. This proved to be a less than intelligent move. Ubuntu is now gone, it comes up on my OS choices menu, but then can't find the menu.lst grub file, or the kernal, or anything else. No "repair" option appears, though i do get a command line screen. I need to reinstall it. As a final kick in the teeth, windows is now confused about my disk space, claiming that i have 33gb used on my c drive (when i click properties in my computer), rather than the 15gb or so i'm actually using (the sum of the numbers i get when i click properties on each of the subfolders in my c drive). I need to correct windows so i can reinstall ubuntu with an adequate amount of memory. Sorry if the information i've given here is insufficient i'm (obviously) no computer scientist.

I should probably mention that i had recently installed a driver to allow ubuntu to read/write ntfs, so i could access the windows partition from it. THis may be the method by which xp managed to delete ubuntu.

---

### Post by amac777 on 2008-10-11
Did you originally install Ubuntu using the "Wubi" method? If so, I believe that method stores all the Ubuntu files on your windows partition. So that would mean you could delete them from within windows. 

Maybe all the files you deleted are in the recycle bin? Can you restore them? (Deleted files being in the recycle bin would explain why your total disk space is higher than it should be.)

---

### Post by zslastman on 2008-10-11
Yes i think i did install it with wubi. The recycle bin is empty, but "ubuntu" does come up in the add/remove programs window. If i try to modify it it just says there was an error and that it may already have been uninstalled, and would i like to take it off the menu.

---

### Post by rlhawk on 2008-10-11
Well, sorry to say, but you just deleted Ubuntu from your computer.  The Wubi method uses your Windows file system if I'm not mistaken.  I'm afraid you'll just have to reinstall it.  I'm sorry.

---

### Post by zslastman on 2008-10-11
I'm resigned to that. The problem is that the poor ghost of ubuntu is still taking up about 20gb of space, which i need if i'm going to reinstall it... I realise i probably deserve this, but my laptop doesn't.

---

### Post by koenn on 2008-10-11
> **zslastman said:**
> I'm resigned to that. The problem is that the poor ghost of ubuntu is still taking up about 20gb of space, which i need if i'm going to reinstall it... I realise i probably deserve this, but my laptop doesn't.

run disk cleanup on the drive (it's somewhere in the properties dialog) and let it do a disk check on boot. While you're at it, defragment the drive.

---

### Post by amac777 on 2008-10-12
This link has lots of helpful info: [https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

From that page:

> How do I manually uninstall Wubi?

Remove C:\ubuntu (C:\wubi in 7.04) and C:\wubildr*.

In Windows XP you need to edit C:\boot.ini and delete the Ubuntu/Wubi line. For Vista, you can use EasyBCD to edit the boot menu. Alternatively you can modify the boot menu via control_panel > system > advanced > startup_and_recovery and pressing "Edit". For Windows 98 you have to edit C:\config.sys, and remove the Wubi block.

To remove Wubi from the add/remove list, delete the registry key: HKLM\Software\Microsoft\Windows\CurrentVersion\Uninstall\Wubi

---

### Post by zslastman on 2008-10-13
Hmmm. I've manually deleted wubi as per the instructions, but the space remains stubbornly taken up.

---

### Post by amac777 on 2008-10-13
There are a number or reasons that your used disk space might appear to be higher than the sum of the files. For example, there could be large hidden files, or corruption on the drive to name two reasons. 

I'm not that familiar with windows XP but you might want to make sure you are viewing hidden files when you look around the drive:

>    1. Open Windows Explorer
   2. Select Tools -> Folder Options -> Check &#8220;Show Hidden Files and Folders&#8221; + Uncheck &#8220;Hide protected operating system files&#8221;


In particular, I'd check in the c:\Recycler folder to see if there are any large hidden files left over in there taking up space. Maybe the large wubi file got moved in there as a hidden file so is still taking up space?

If not, there are probably some disk checking tools you can run for XP to see where the file space is being taken up. But again, I'm not quite sure how to do this in Windows.

---

### Post by zslastman on 2008-10-15
AHA!!! Okay i think i found the missing memory. Windows has stored it as a hidden folder (actually a "protected system folder", thanks for pointing out that box). Now i'm very wary of just deleting it, but it weighs in at 14gb. Anyone know if this is safely deletable? I know windows probably isn't the specialty of most people here...

---

### Post by amac777 on 2008-10-15
what is the folder directory, and what are the contents? (names of files etc)

---

### Post by zslastman on 2008-10-20
Yeah sorry i really should have posted that. Regardless i got help from a more capable friend, and was able to delete all of it. **Problem solved**, thanks guys.

---

