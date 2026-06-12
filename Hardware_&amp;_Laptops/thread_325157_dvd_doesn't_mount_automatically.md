---
title: "dvd doesn't mount automatically"
date: 2006-12-25
forum: Hardware &amp; Laptops
---

### Post by Selmi on 2006-12-25
hi

i have 2 drives in my computer, one is simple cd reader (/dev/hdd) and one is dvd writer (/dev/hdb)

when i put cd to cd drive then in gnome it is detected and icon appears on desktop and also soem action happens (cdaudio start play, data cd content will appear in file browser)

when i put anything to dvd drive nothing happens. but when i open terminal and make 'mount /dev/hdb' manually then dvd is mounterd and its icon appears on screen - but i must unmount also manually, rightclicking on icon and unmount like this will show error mesage

what can be wrong with it? btw it worked correctly before, it stopped 2 days go. i checked /etc/fstab and for both drives there are same lines. also i searched for /dev/hdb and /dev/hdd in /etc and i didn't found anything what would be different...

please help...

EDIT: all this happens on ubuntu 6.06 LTS DapperDrake with all updates until today

---

### Post by xyz on 2006-12-25
You did run this
```
sudo mount /media/cdrom0/ -o unhide

```
and then:
```
sudo mount -a
```
Perhaps post the output:
```
sudo /etc/fstab
```
just to have a look-see!

---

### Post by Selmi on 2006-12-25
lines in etc fstab are:

/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto,utf8     0       0
/dev/hdb        /media/cdrom1   udf,iso9660 user,noauto,utf8     0       0

i found that when i open filebrowser manually and choose this dvd drive in list onleft side then icon appears on desktop and everything works.

when i tried to mount manually it also appears. it seems everything works, only icon doesn't appear

also another thing. when i played dvds then after i inserted dvd to drive totem appeared and started to play dvd. now when i run totem manually and in menu choose 'play disk...' then it ejects dvd and tells me that there is no plugin to play dvds.... mplayer plays dvds fine, but of course without menu

and as i said in previous post all this happens only with /dev/hdb. /dev/hdd still works like before without any problem. i also restarted computer few times in hope it will help but it didn't

---

