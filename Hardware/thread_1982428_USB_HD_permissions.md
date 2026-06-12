---
title: "USB HD permissions"
date: 2012-05-18
forum: Hardware
---

### Post by jlh68 on 2012-05-18
I have a WD Elements 320-GB USB Hard Drive that I cannot copy file to it.  I get the message that I do not have permission to do it. When I go to permissions it shows that it is owned my "root" and not "john"

The USB HD is a 320_GB formatted in .ext4 file system.  Now I have a 40-GB and an 80-GB that came out of laptops that act just like a flash drive and I can move files with ease.  I want to make this 320-GB HD to work the same way.

What do I do.  Reformat to MSDOS, or VFAT?  Of leave alone and make permissions changes?  How do I change the permission?  In any case right now I have almost 300-GB of storage I can not use. Please if you can help me I would appreciate it.

---

### Post by jlh68 on 2012-05-18
I tried to format to FAT32.  NO luck and now I get the attached message.  I am not sure what to do with this drive as it is useless as it now stands.

---

### Post by netopalis45 on 2012-05-18
The way I get around that is by going to the /media folder and using the sudo chown command so you are now the owner of the drive. You should be able to transfer file correctly once you do that.

---

### Post by jlh68 on 2012-05-21
Cannot reformat still have problems with the hard drive software or internal architecture. Unit came with NTDS and some kind of WD software.  Tried to reformat to MSDOS, then Ext4 then to what ever.  I cannot get the downloaded WD restore programs to even work using Win 7.  This external HD is now worthless.  It is the second one I have had, the first failed to connect to any operating system and WE replaced it with this one.

I Just want to find a 320-GB or more external HD that will work like a flash drive in the movement of files.

---

