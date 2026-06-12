---
title: "&quot;Error while copying to &quot;Iomega HDD&quot; The destination is read-only."
date: 2009-06-03
forum: Hardware
---

### Post by elelias on 2009-06-03
Hi everybody, ubuntu n00b talking here...

I just bought a 1 TB iomega HDD, but I can't copy anything in it, everytime I try I get:

 "**Error while copying to "Iomega HDD". The destination is read-only**."

when looking at the permissions, it says:
-----------------------
[B]Owner: 99
Group: 99
Selinux context: unknown
Last changed: unknown

You are not the owner so you can't change the permissions.[/B]
-----------------------

I tried "chmod u+rw /media/iomega/Iomega\ HDD but it does not change anything (which makes sense since apparently I cant change permissions). 

I haven't found anything useful out there so I'm turning to you guys, any ideas? thanks!

elelias.

---

### Post by dePeatrick on 2009-07-22
I have the same problem here too, anyone any idea/

---

### Post by bryonak on 2009-07-22
What's the output of this terminal command: ```
sudo ls -ahl /media/iomega
```
It will simply list the contents of this folder with it's associated owners/permissions.


Chances are it's formatted as FAT32, which doesn't support permissions.
To find out, you have to know which device interface it uses. Is it connected via IDE/SATA or USB?
If it's IDE/SATA, please post the output of ```
sudo fdisk -l
```

If you prefer a GUI, start the menu -> System -> Administration -> System Monitor -> File Systems and report the type listed there. Still the fdisk command from above is a bit more informative.


Not only permissions are important, but the mount options you use for a file system... it usually works well automatically, but more of that after we know what we're dealing with here ;)

---

### Post by edwardtagg on 2012-05-31
Error while copying to "Kingston" (USB) The destination is read-only
 	I have been using this USB for 1 month with no problems but now it wont let me copy any file (large or small) into it ...
 	I right click and PERMISSIONS says ..."The permissions of "Kingston" could not be determined"
 	This started after I did some updates with the orange triangle at  the top left of the screen.... Updates always say that errors occur in  part of the process...? confused....
 	Please help - I am a newbie, and can only do basic terminal language....
 	You are using Ubuntu 10.04 LTS
	- the Lucid Lynx - released in April 2010 and supported until April 2013. (copied from "ABOUT UBUNTU")
 	This problem plagues other people, and all the other forums seem to fail to help?
 	Really appreciate the help - bless - Edward James Tagg

---

### Post by coffeecat on 2012-06-01
Old thread closed.

@edwardtagg, you will get answers in the thread you have started with the same question. Please do not post the same question in different places.

---

