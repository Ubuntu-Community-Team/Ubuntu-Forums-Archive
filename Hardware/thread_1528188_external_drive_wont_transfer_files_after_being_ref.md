---
title: "external drive wont transfer files after being reformatted to ext3"
date: 2010-07-10
forum: Hardware
---

### Post by drunk-wolf on 2010-07-10
I recently bought this drive [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6052655&CatId=136](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=6052655&CatId=136) (Hitachi Simpletech 1TB) and reformatted it to ext3 with gparted to get rid of the crap that came pre-installed on it, after that I tried to transfer some files to it and I get an error message.... since then I have tried reformatting it to ext2 ext3 ext4 and Fat32, the only one that will allow file transfer is Fat32, it will read and write fine with Fat32, on both of my Linux machines, but wont show up on my friends windows machine. any ideas what could be causing this or how to correct it??

---

### Post by ajgreeny on 2010-07-10
What exactly is the error message you receive?  It's a bit difficult to offer a solution when we don't have the full story.

I assume you have removed the drive properly and then re-connected it, after formatting to any of those format types.  Normally the disk would then be automounted to a folder in /media and with permissions for the current user.

---

### Post by drunk-wolf on 2010-07-10
The error message it gives when formatted to ext3 is "the folder "Lol" cannot be copied because you do not have permissions to create it in the destination." it also looses about 60 GB of space out of 931 GB that Fat32 doesn't.

---

### Post by ajgreeny on 2010-07-11
You will need to change the owner of that folder with the terminal and the command ```
sudo chown user:user /full/path/to/folder
```
You will need to find the path by looking in /media for the disk's folder name, and it will be something like **/media/diskname/Lol** but should be easy enough for you to find.

However, windows users will not be able to see this disk at all, I'm afraid, as windows can not access any ext# file systems.  If you want it to be multi OS readable, format it to ntfs or fat32.

---

### Post by drunk-wolf on 2010-07-11
yeah, I know it won't be readable under windows, but I had too many problems when I had it as Fat32, and for some reason ntfs wasn't available in gparted, got it to work with ext3 by using "gksu nautilus /media/disk" I'll try what you suggested though because it's a pain in the *** to have to use command line every time I plug in the drive. any idea why I lose 60 Gb of space with ext3 and not in Fat32??

---

### Post by drunk-wolf on 2010-07-11
I tried it as "sudo chown wolf:wolf /full/media/disk" and got a "no such file or directory" error, theres nothing after disk, just /media/disk is there something I'm missing??

---

### Post by ajgreeny on 2010-07-12
With the external disk attached and mounted, look in /media to see what the mount folder is called; it is never going to be called **/full/media**, that was just my example of the full pathway that would be needed.

OK it looks as if it is called /media/disk, so you need to use ```
sudo chown wolf:wolf /media/disk
``` ie no **/full** in the pathway.  That will make the folder belong to you as user wolf.

As to the 60 GB missing, no they are not missing but are the so called reserved space on the disk.  All journaled file systems, ext3, ext4, and most linux types I think, reserve 5% for actions that are needed when carrying out file-system checks and so on.  It is possible to change or remove that reserve with the cli utility **tune2fs** if you wish (see man tune2fs).

---

### Post by drunk-wolf on 2010-07-12
thanks for your help, I found this 
sudo chown -R wolf:wolf /media/disk
ls -la /media

in another thread with a similar problem to mine, seems to have done the trick, and thanks for the explanation about the journaled file systems, makes sense.

---

