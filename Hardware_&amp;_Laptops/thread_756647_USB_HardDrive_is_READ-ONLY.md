---
title: "USB HardDrive is READ-ONLY ???"
date: 2008-04-16
forum: Hardware &amp; Laptops
---

### Post by cartooncartoon on 2008-04-16
Hello ,,, i have a problem formatting a hard dirve that used to be ntfs 

its 120gb hooked up with usb and there seems to be a folder i cannot delete on it even after formatting the drive in different ways. also the drive appears to be read-only and i cannot write to it either please help me !! im a noob again :(

---

### Post by linuxisfree on 2008-04-16
do you have ntfs3g or ntfs config installed in your system? If not, then install them.
 
In ntfs config, there will be a check box that says something about write to ntfs (or something like that, can't remember the exact words), make sure that it is checked.
 
Hope that'll work.
 
EDIT: "used to be NTFS" ? what is it now?

---

### Post by cartooncartoon on 2008-04-16
well i used gparted and tried to make it ex3 , then that didn't really work , cause there was a folder still there that i couldnt del , so i tried to use terminal command rmdir blah blah and it was gone , then it came back , so i formated it to fat32 , then to ex3 , then 2 ex2 i think its ex2 now lol i dont' know what the hell im doing

---

### Post by cartooncartoon on 2008-04-16
i do know its not nfts though , and this ntfs config thingy wont' help me this time , but thanks for that it will be useful in the future

---

### Post by linuxisfree on 2008-04-16
> **cartooncartoon said:**
> well i used gparted and tried to make it ex3 , then that didn't really work , cause there was a folder still there that i couldnt del , so i tried to use terminal command rmdir blah blah and it was gone , then it came back , so i formated it to fat32 , then to ex3 , then 2 ex2 i think its ex2 now lol i dont' know what the hell im doing
 
Kinda messy!:lolflag:
 
Seriously though, how about the permissions? who "OWNS" the drive? (you can check it in the properties-->permissions when you right click.)
 
EDIT: to MODS, sorry for replying thrice, something wrong with my connection, please just delete my other 2 posts, Thanks!

---

### Post by linuxisfree on 2008-04-16
> **cartooncartoon said:**
> well i used gparted and tried to make it ex3 , then that didn't really work , cause there was a folder still there that i couldnt del , so i tried to use terminal command rmdir blah blah and it was gone , then it came back , so i formated it to fat32 , then to ex3 , then 2 ex2 i think its ex2 now lol i dont' know what the hell im doing
 
Kinda messy!:lolflag:
 
Anyway, who "owns" the drive? (right-click, properties > permissions)

---

### Post by linuxisfree on 2008-04-16
> **cartooncartoon said:**
> well i used gparted and tried to make it ex3 , then that didn't really work , cause there was a folder still there that i couldnt del , so i tried to use terminal command rmdir blah blah and it was gone , then it came back , so i formated it to fat32 , then to ex3 , then 2 ex2 i think its ex2 now lol i dont' know what the hell im doing
 
Who "owns" the drive? (right click the drive then go to properties then permissions)

---

### Post by cartooncartoon on 2008-04-16
oh... its root ...

---

### Post by cartooncartoon on 2008-04-16
i tried sudo chown username: /media/disk  that doesnt' seem to do anything

---

### Post by linuxisfree on 2008-04-16
ok, when you tried the rmdir command, did you put the word "sudo" before it?
 
like the ff:
 
```
sudo rmdir <insert location of folder here>
```

---

### Post by cartooncartoon on 2008-04-16
yes with sudo

---

### Post by cartooncartoon on 2008-04-16
the directory goes away for now , but i still cannot write to that drive

---

### Post by linuxisfree on 2008-04-16
> **cartooncartoon said:**
> i tried sudo chown username: /media/disk that doesnt' seem to do anything
 
Still root? how about you try this...
 
```
sudo chown -R <username>:<group> /media/disk
```

---

### Post by cartooncartoon on 2008-04-16
i don't know what my group is... but when i did that command without group ,,, it didn't do anything hah i suck

---

### Post by linuxisfree on 2008-04-16
You can see what group your username is a part of in System-->Administration(?)-->Users and Groups.
Although, usually it is the same as your username (by default)
 
PS: YOU DON'T SUCK!!!

---

### Post by MrFSL on 2008-04-16
Is it possible that the name of this folder is "lost+found?"

---

### Post by cartooncartoon on 2008-04-16
ok i added myself to the group xander and i added root to that group , i also added me to root group too just in case... so now i can access the permissions for the drive , which i couldn't' do before , but i cannot change them because i am not the owner .. so i guess i just have to figure out how to set the owner correctly and hope i didn't mess things up too much

---

### Post by cartooncartoon on 2008-04-16
yes it was called lost+found ...

---

### Post by linuxisfree on 2008-04-16
> **cartooncartoon said:**
> ok i added myself to the group xander and i added root to that group , i also added me to root group too just in case... so now i can access the permissions for the drive , which i couldn't' do before , but i cannot change them because i am not the owner .. so i guess i just have to figure out how to set the owner correctly and hope i didn't mess things up too much
 
Well, now you can do this:
```
sudo chown -R <username>:<group> /media/disk
```
 
to change to owner to your username:D

---

### Post by cartooncartoon on 2008-04-16
awesome, totally awesome!! way to go hamilton !! 

its works !! i have another 120gb !! thank you so much !!

---

### Post by Tomatz on 2008-04-16
Just do this in a terminal to open the drive with r/w permissions:

```
gksu nautilus /media/**[drive number/name e.g sda1]**
```

You can make a script with the code and put it into /usr/bin then run it from a desktop shortcut/menu launcher ;)

---

### Post by erginemr on 2008-04-16
For more info on the lost+found directory, please refer to:
[http://ubuntuforums.org/showthread.php?t=752895](http://ubuntuforums.org/showthread.php?t=752895)

For all that I know, it is an important part of the Linux directory tree, is used by fsck (file system check) to dump the recovered files. There should also be another lost+found directory under your root drive and it is normal to have it.

---

### Post by linuxisfree on 2008-04-16
> **erginemr said:**
> For more info on the lost+found directory, please refer to:
[http://ubuntuforums.org/showthread.php?t=752895](http://ubuntuforums.org/showthread.php?t=752895)

For all that I know, it is an important part of the Linux directory tree, is used by fsck (file system check) to dump the recovered files. There should also be another lost+found directory under your root drive and it is normal to have it.


Hey, thanks for the link. Very useful. My only question though, is what was it doing in his 120gb HDD? I don't think that's where his linux is installed...

---

### Post by erginemr on 2008-04-16
My best guess would be that your system is somehow setup to check the integrity of this drive as well. 

I don't have any experience with removable USB hard drives, but **for fixed hard drives**, the system creates this folder if fsck is allowed to do regular checks on them via a 1(on)/0(off) bit at the end of the line corresponding to this drive in the **/etc/fstab **file.

---

### Post by MrFSL on 2008-04-16
> **linuxisfree said:**
> Hey, thanks for the link. Very useful. My only question though, is what was it doing in his 120gb HDD? I don't think that's where his linux is installed...

The original poster said that he/she had formatted the drive first ext3 then ext2... hence the appearance of lost+found.

---

