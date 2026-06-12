---
title: "EEE PC SD mount issues + Nautilus"
date: 2008-07-16
forum: Hardware
---

### Post by thorwood on 2008-07-16
Just purchased a EEE PC. Naturally i put ubuntu on it.
I fix most of the bugs, but two of them I cannot fix.

1. SD card will not mount. All that comes up is can't mount file.

2. This odd problem comes up too. Some times when I boot up a warning comes up about the bonobo-activation-server needs to be killed and then restart Nautilus. After I started getting that message, when I hit the off icon on the GNOME panel, all the panels disappear.

Im leaving on a trip so i need to solve this problem fast!

---

### Post by thorwood on 2008-07-16
aite fixed the SD card. Just Nautilus left

---

### Post by Kissinggate on 2008-08-18
Ne to Ubuntu. I searched like hell. This works:

sudo nano /etc/fstab

gives
# /dev/sda1
UUID=1c098a4f-da39-46c4-8c4b-d311f8d38f6d /               ext3    relatime,erro
$# /dev/sda5
UUID=94b0f638-bdc0-4f29-a90f-9dd8c70f5eb2 none            swap    sw           
/dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sdb1     /media/cdrom0   udf,iso9600 user,noauto,exec      0       Osd card

change the three last lines by adding 2 #-signs:

# /dev/sda1
UUID=1c098a4f-da39-46c4-8c4b-d311f8d38f6d /               ext3    relatime,erro
# /dev/sda5
UUID=94b0f638-bdc0-4f29-a90f-9dd8c70f5eb2 none            swap    sw           
# /dev/sdb1       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd0       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
# /dev/sdb1     /media/cdrom0   udf,iso9600 user,noauto,exec      0       Osd card

Finally, after two days I got my card!!

---

### Post by RedPandaFox on 2008-08-18
> **thorwood said:**
> 
2. This odd problem comes up too. Some times when I boot up a warning comes up about the bonobo-activation-server needs to be killed and then restart Nautilus. After I started getting that message, when I hit the off icon on the GNOME panel, all the panels disappear.


Iv never heard of this problem on an Eee PC, Maybe try reinstalling gnome?

---

### Post by Meta_Tagg on 2008-10-06
Maybe you can install pmount and ivman.. it worked for me.. :)

open terminal

sudo apt-get install pmount ivman


/ Meta_Tagg

---

