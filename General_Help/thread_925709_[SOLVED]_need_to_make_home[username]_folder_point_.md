---
title: "[SOLVED] need to make /home/[username]/ folder point to folders in vista partition"
date: 2008-09-20
forum: General Help
---

### Post by pjizz on 2008-09-20
hi all,

i've got a (finally) stable setup dual booting vista with hardy 8.04.1.

i've successfully edited the fstab file to automount the vista ntfs partition at boot (see code), so everything works fine.

the only problem is, everytime i want to save a file, i have to navigate through a lot of folder structure.  so i was wondering if there was a simple way to make the folders in the /home/[username]/ directory, music, pictures, documents, point to the similar folders, my music, etc, in the vista partition.  

the reason i really want to stick the media files and such in the vista partition is i still have to use windows quite often, and I therefore need them stored in the NTFS partition, since if they were in the ext3 filesystem windows wouldnt be able to access them.

i've looked around and found out about something called symbolic linking, but couldn't come up with any solution to my issue, so here is a post asking the faithful community!  all help lavishly rewarded with thank you's!



```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=72507c0c-c9d9-4cf2-aba6-1bf4d8b7e09e /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=6a115341-8ef6-4a02-a5c6-20cadd483e49 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3	/media/Vista_part ntfs	defaults	0	0
```

---

### Post by mb_webguy on 2008-09-20
The preferred way to share files between operating systems on a dual boot setup is to install each OS on a small partition just large enough for the operating system and installed applications, and then have a separate partition for storing your files.  This way, the operating systems aren't exposed to each other, and you don't risk screwing up one operating system while using the other.  Vista can reside comfortably on a 25GB partition, while Ubuntu can live happily on an 8GB partition.  Add a small swap partition and preferably a small (<1GB) home partition for Ubuntu, and that leaves the rest of your drive for file storage.

Having said that, if you have your Vista partition mounted in Ubuntu, you just need to create some symbolic links (similar to shortcuts in Windows) to the folders from your home directory.  Open the terminal and type "ln -s /path/to/folder linkname" for each folder, replacing /path/to/folder with the path to the Windows folder, and linkname with what you want to call the link, such as "Documents".

---

### Post by unutbu on 2008-09-20
To make /home/$USER/music be a symbolic link to /media/Vista_part/music:

If /home/$USER/music already exists use nautilus (or your prefered file manager) to move the files over to /media/Vista_part/music. Then remove the directory /home/$USER/music.

Open a terminal and type
```

ln -s /media/Vista_part/music /home/$USER/music

```
This will create the symbolic link /home/$USER/music.
Now when you save files in /home/$USER/music Ubuntu will actually write the files to 
/media/Vista_part/music.

You might also be interested in ext2ifs ([http://www.fs-driver.org/](http://www.fs-driver.org/)). This is a driver which allows Windows to read and write to ext3 filesystems.

---

### Post by pjizz on 2008-09-21
thanks guys...yes, next time I think i'll have a "media" partition.  but for now, this info works great.  thanks for the code esp.

pjizz

---

