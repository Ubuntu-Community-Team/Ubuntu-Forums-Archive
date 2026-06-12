---
title: "zcat destroying my usb disk?"
date: 2008-11-29
forum: Hardware
---

### Post by OmnificienT on 2008-11-29
Hello,

I've been following [this]("http://wiki.debian.org/DebianAcerOne") tutorial. What I notice was that zcat would [COLOR="Red"]**only**[/COLOR] work after having done sudo su. Just using sudo in front of the command would tell me: "acces denied". 

Using this has, for Ubuntu, messed up the disk quite badly. Doing fdisk -l shows me this:
```

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sdf1   ?      838545      902718   123339962   78  [onbekend]
Partitie 1 heeft verschillende fysieke/logische beginpunten (niet-Linux?):
     fysiek=(518, 102, 15) logisch=(838544, 58, 50)
Partitie 1 heeft verschillende fysieke/logische eindpunten:
     fysiek=(743, 0, 62) logisch=(902717, 41, 15)
Partitie 1 eindigt niet op een cilindergrens.
/dev/sdf2   ?      112610      314401   387841909+  10  OPUS
Partitie 2 heeft verschillende fysieke/logische beginpunten (niet-Linux?):
     fysiek=(205, 7, 0) logisch=(112609, 34, 14)
Partitie 2 heeft verschillende fysieke/logische eindpunten:
     fysiek=(920, 235, 50) logisch=(314400, 21, 34)
Partitie 2 eindigt niet op een cilindergrens.
/dev/sdf3   ?      486359      985639   959615034   8b  [onbekend]
Partitie 3 heeft verschillende fysieke/logische beginpunten (niet-Linux?):
     fysiek=(260, 125, 54) logisch=(486358, 38, 56)
Partitie 3 heeft verschillende fysieke/logische eindpunten:
     fysiek=(893, 46, 60) logisch=(985638, 2, 35)
Partitie 3 eindigt niet op een cilindergrens.
/dev/sdf4   ?        8712       10878     4161536    a  OS/2 opstartmanager
Partitie 4 heeft verschillende fysieke/logische beginpunten (niet-Linux?):
     fysiek=(269, 111, 50) logisch=(8711, 61, 31)
Partitie 4 heeft verschillende fysieke/logische eindpunten:
     fysiek=(0, 0, 0) logisch=(10877, 12, 36)
Partitie 4 eindigt niet op een cilindergrens.

Partitietabel-items liggen niet in schijfvolgorde.

```

Gparted refuses to format the drive.

Windows however is happy to accept the drive.

I thought the drive (which was quite cheap) would be malfunctioning. After trying a different usb stick, that one had the same problems.

How could this have happened, and how do I fix the usb stick?

Thank You,

OmnificienT

---

### Post by cdtech on 2008-11-29
The drive would have to be unmounted to format through Ubuntu. If your trying to install the Ubuntu to the USB stick try the "System > Administration > Create USB startup disk".

I think if you unmount the stick you can reformat.

---

### Post by OmnificienT on 2008-11-29
Gparted will give me the following error:

```

GParted 0.3.8

Libparted 1.8.9

/dev/sdf1 (fat16, 1.87 GiB) verwijderen van /dev/sdf  00:00:00    ( SUCCESS )
     	
/dev/sdf1 kalibreren  00:00:00    ( SUCCESS )
     	
pad: /dev/sdf1
begin: 0
eind: 3915775
grootte: 3915776 (1.87 GiB)
partitie verwijderen  00:00:00    ( SUCCESS )

========================================

Primaire partitie #1 (fat16, 1.86 GiB) aanmaken op /dev/sdf  00:00:00    ( ERROR )
     	
lege partitie aanmaken  00:00:00    ( ERROR )
     	
pad: /dev/sdf1
begin: 0
eind: 3903794
grootte: 3903795 (1.86 GiB)
libparted meldingen    ( INFO )
     	
/dev/sdf: unrecognised disk label

========================================

```

---

### Post by OmnificienT on 2008-11-29
After tinkering a bit, I got it to format, however zcat insists on disrupting the filesystem completely. How do I fix that?

---

