---
title: "Arrrgh!  I altered the mount point of my windows partition"
date: 2009-01-04
forum: Hardware
---

### Post by mpc350 on 2009-01-04
Using the gnome properties submenu.  Under the "Volume" tab.  I wanted it to automount on the desktop so I could easily access the music in my windows partition so I changed the mount point to /home/myusername/Desktop and now it wont mount at all, and I can't get back to the mount point options to undo what I did.  I hate it when start thinkin' I know what I'm doing and obviously don't.

Any help?
Thanks

---

### Post by ajgreeny on 2009-01-04
I'm not sure quite what you mean byt the "gnome properties menu" but think perhaps you are talking about the right click Properties of the mounted drive in nautilus.  If so check this out.
Is the windows partition where your music is located shown in your /etc/fstab file as mounting elsewhere?  If so you may need to edit that file to get things as you want them, or simply set things back to the way they were.

Post the output of ```
cat /etc/fstab
``` here and we may have more clues.

---

### Post by mpc350 on 2009-01-04
You are right... That's what I did.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=c9c84a36-7b9b-48bf-a42f-141acf6517c1 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=cdc8d701-35f5-4295-8ed1-7e836e09b3ee none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

SDA2 which dosent appear to be listed here is my windows partition which will no longer mount

---

### Post by ajgreeny on 2009-01-04
OK, so try editing the /etc/fstab file and adding this line to it
```
/dev/sda2       /home/username/Desktop  ntfs    nls=utf8,umask=0222 0       0
```
with ```
gksudo gedit /etc/fstab
```  Save the file and then do ```
sudo mount -a
```
For neatness you may like to make the mount point */home/username/Desktop/Windows* but just make a folder of that name in Desktop first or it will not work.

---

### Post by mpc350 on 2009-01-04
so the basics of sudo mount -a are to mount all available drives on the desktop?  

it definitely worked to remount the volume that i couldn't before.  i immediately went to the properties submenu and got rid of the mount point drivel i put in that caused the problem to begin with.  but... how do you use the GUI version of mount point, file system and mount options?  or is the problem just that I didnt include the correct parameters to mount correctly.

I'm trying the rest, rebooting

Thanks.
Matt

---

### Post by ajgreeny on 2009-01-04
sudo mount -a simply mounts all the partitions listed in /etc/fstab

Sorry, I haven't got a clue about using the GUI to do that mount point change you wanted, it's something I've never done.

---

