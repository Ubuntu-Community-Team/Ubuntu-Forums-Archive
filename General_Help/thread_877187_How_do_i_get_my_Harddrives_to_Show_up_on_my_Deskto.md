---
title: "How do i get my Harddrives to Show up on my Desktop?"
date: 2008-08-01
forum: General Help
---

### Post by robotman5 on 2008-08-01
i need help doing it Every time i  try to copy it it thinks im tryin to Mount it Please help!:(

---

### Post by dexter.deepak on 2008-08-01
please be more clear.
you want an auto-mount or just show the mounted drives on the desktop ?

---

### Post by robotman5 on 2008-08-01
Just Show the Mounted Dirves on the Desktop:guitar:

---

### Post by dexter.deepak on 2008-08-01
type in a terminal :
```

gconftool-2 --type bool --set /apps/nautilus/desktop/volumes_visible 'true'
```

---

### Post by Ryadt on 2008-08-01
Double posting is against forum rules.
[http://ubuntuforums.org/showthread.php?t=877164](http://ubuntuforums.org/showthread.php?t=877164)

---

### Post by robotman5 on 2008-08-01
Dex it doesnt Do anything!  and it says Bool is not a Command!!!

---

### Post by dexter.deepak on 2008-08-01
thats really strange :shock:
try :
```
gconf-editor
```
now goto apps -> nautilus -> desktop
here check the volumes-visible checkbox.

---

### Post by TreeFinger on 2008-08-01
Create a soft link in ~/Desktop who's target is the harddrive.

---

### Post by robotman5 on 2008-08-01
Nop Still wont do it i tryed the gconf-editor but it still wont.:confused:

---

### Post by LowSky on 2008-08-01
drive should just show up, can you acces the drive now if not you need to mount the drive first. it wont work unless the drive is mounted.

is it a Windows Drive?

---

### Post by dexter.deepak on 2008-08-01
you are using gnome... right ?
then maybe you have to install gconf-editor ..i thought its there by default.
```
 sudo apt-get install gconf-editor
```

---

### Post by robotman5 on 2008-08-01
Thank you Lowsky!!!

---

### Post by LowSky on 2008-08-01
for what?

---

### Post by robotman5 on 2008-08-01
you told me to Mount the Volume Drive *its Windows XP harddrive* and it worked!

---

### Post by smooth3006 on 2008-08-01
how do i keep the drives mounted on the desktop after reboot ? :confused:

---

