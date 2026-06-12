---
title: "gnome commander problem with copying"
date: 2008-11-12
forum: General Help
---

### Post by Stjepan_esa on 2008-11-12
Hello, I'm newbie to ubuntu.
I have a problem with gnome commander. Can't copy any files to mounted ntfs partitions or to external hard disk. In fact, with mouse, I can do it, but with F5, no chance.
It says for example

"The directory 'diskE' doesn't exist, do you want to create it?"

My fstab looks like this:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=e1900c74-525c-478f-9c75-95b0b0839942 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=12322C4DBD81B3B9 /media/diskD    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda6
UUID=48C8B13B3A0A2044 /media/diskE    ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda1
UUID=F830BF0930BECDBE /media/windows  ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda8
UUID=b4b88c1b-98bc-440a-9bff-c43f277e505f none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


D and E disk from Windows are mounted to /media/diskD and /media/diskE directories.

Sorry if it's a dumb question.
Please help.

---

### Post by geirha on 2008-11-12
Your entries are using the (old) ntfs driver which doesn't support writing. Replace ntfs with (the newer) ntfs-3g which supports writing. After doing that change in fstab, unmount the drives and then mount them again.
```

sudo umount /media/{windows,diskD,diskE}
sudo mount -a

```

---

### Post by Stjepan_esa on 2008-11-12
How to change that ntfs driver? :-)
Thanks a lot

---

### Post by Idefix82 on 2008-11-12
Replace the words "ntfs" in your fstab by "ntfs-3g" (without the inverted commas). So it should look like this:
```
proc /proc proc defaults 0 0
# /dev/sda7
UUID=e1900c74-525c-478f-9c75-95b0b0839942 / ext3 relatime,errors=remount-ro 0 1
# /dev/sda5
UUID=12322C4DBD81B3B9 /media/diskD ntfs-3g defaults,umask=007,gid=46 0 1
# /dev/sda6
UUID=48C8B13B3A0A2044 /media/diskE ntfs-3g defaults,umask=007,gid=46 0 1
# /dev/sda1
UUID=F830BF0930BECDBE /media/windows ntfs-3g defaults,umask=007,gid=46 0 1
# /dev/sda8
UUID=b4b88c1b-98bc-440a-9bff-c43f277e505f none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
```

---

### Post by geirha on 2008-11-12
Edit /etc/fstab by hitting Alt+F2 to get the Run-dialog, and run "gksu gedit /etc/fstab". It will ask for your password to do administrative tasks (which this is)
```

# Change
UUID=12322C4DBD81B3B9 /media/diskD [COLOR="Red"]ntfs[/COLOR] defaults,umask=007,gid=46 0 1
# to
UUID=12322C4DBD81B3B9 /media/diskD [COLOR="Blue"]ntfs-3g[/COLOR] defaults,umask=007,gid=46 0 1

```

Do that for the other two windows file-systems as well.

---

### Post by Stjepan_esa on 2008-11-12
OK, I did it with 

```
sudo apt-get install ntfs-config
```

and after enabling writing for internal and external partitons, it said
---remountnig---
DO I need to remount the partitons manually?
For now, it still doesn't work.

---

### Post by Stjepan_esa on 2008-11-12
Works great, after manual remountnig.
Thank you a thousand times.

---

### Post by geirha on 2008-11-12
> **Stjepan_esa said:**
> OK, I did it with 

```
sudo apt-get install ntfs-config
```

and after enabling writing for internal and external partitons, it said
---remountnig---
DO I need to remount the partitons manually?
For now, it still doesn't work.

Based on your /etc/fstab, only members of the group with id 46 (gid=46) have write access. You can add your user as the owner of the drives by adding the option uid=*yourusername*

```

UUID=12322C4DBD81B3B9 /media/diskD ntfs-3g defaults,umask=007,gid=46 0 1
#to
UUID=12322C4DBD81B3B9 /media/diskD ntfs-3g defaults,umask=007[COLOR="Blue"],uid=*yourusername*[/COLOR],gid=46 0 1
```

Replacing *yourusername* with your actual username of course :)

---

