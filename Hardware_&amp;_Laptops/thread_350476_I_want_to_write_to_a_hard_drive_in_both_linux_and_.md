---
title: "I want to write to a hard drive in both linux and windows"
date: 2007-01-31
forum: Hardware &amp; Laptops
---

### Post by mattgaunt on 2007-01-31
Hey everyone

I have a spare hard drive and this is what i would like to happen and jus wanted some advice on what people think i should do

Basically i want to use this hard drive to have all my music, documents, pictures, jus everything that i would and can use in both linux and windows.

Now i was under the impression that this hard drive would have to be FAT32 but i read somewhere that it can be NTFS and both linux and windows can then read and write to it, so is this possible??

Also i want to install windows vista alongside windows xp and ubuntu, reason for keepin xp is because i do not trust microsoft and DRM together with vista

So yeah if i install windows vista isnt it goin to kick my grub boot out of the system??

Anyway help would be great

Thanks alot

Matt

---

### Post by loserboy on 2007-01-31
Fat32 works fine and thats what i do, but i seen people using fs-drive, but idunno anything about it.

i did a quick search maybe this will help you
[http://www.ubuntuforums.org/showthread.php?t=217009&highlight=writing+to+ntfs](http://www.ubuntuforums.org/showthread.php?t=217009&highlight=writing+to+ntfs)

now about installing vista.
I think the installer works the same as xp where if you install it after grub it will just delete grub.

---

### Post by AstarothCY on 2007-01-31
You could use ext3 for the shared partition, [Fs-driver]("http://www.fs-driver.org/") works just fine.

---

