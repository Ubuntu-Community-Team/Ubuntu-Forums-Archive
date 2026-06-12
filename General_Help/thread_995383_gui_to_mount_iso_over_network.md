---
title: "gui to mount iso over network?"
date: 2008-11-27
forum: General Help
---

### Post by m_a_b on 2008-11-27
I have a NAS setup with several iso cd images on it.  I would like to be able to mount those images in ubuntu using a gui, but have tried a few different methods and none of them work.  They only work if I copy the image to the local computer first.

The most promising method is to use a nautilus script to mount and unmount (so I can just browse to the iso, right click, and mount) but I am new to ubuntu and don't really know how or if the script can be edited so that I can mount an iso on a windows share.  I was reading something that said I had to mount the file system first???

Anyways, can someone help?  Here are the scripts:

mount.sh
```
#!/bin/bash
# mount

gksudo -k /bin/echo "got r00t?"

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

sudo mkdir "/media/$BASENAME"

zenity --info --title "ISO Mounter" --text "$BASENAME e $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS"


if sudo mount -o loop -t iso9660 $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS "/media/$BASENAME"
then
if zenity --question --title "ISO Mounter" --text "$BASENAME Successfully Mounted. Open Volume?"

then
nautilus /media/"$BASENAME" --no-desktop
fi

exit 0
else
sudo rmdir "/media/$BASENAME"

zenity --error --title "ISO Mounter" --text "Cannot mount $BASENAME!"

exit 1
fi
```

unmount.sh
```
#!/bin/bash
# unmount

gksudo -k /bin/echo "got r00t?"

BASENAME=`basename $NAUTILUS_SCRIPT_SELECTED_FILE_PATHS .iso`

sudo umount "/media/$BASENAME"

sudo rmdir "/media/$BASENAME"

zenity --info --text "Successfully unmounted /media/$BASENAME"

exit 0
```

---

### Post by m_a_b on 2008-12-03
bump

---

### Post by Mike The KID on 2010-06-14
I am trying to do the same thing, were you ever able to get something to work?

---

### Post by hovrashko on 2011-03-17
> **Mike The KID said:**
> I am trying to do the same thing, were you ever able to get something to work?

check this thread [http://ubuntuforums.org/showthread.php?p=10572251#post10572251](http://ubuntuforums.org/showthread.php?p=10572251#post10572251)

---

