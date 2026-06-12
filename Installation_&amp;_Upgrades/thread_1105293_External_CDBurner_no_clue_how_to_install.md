---
title: "External CDBurner/ no clue how to install"
date: 2009-03-24
forum: Installation &amp; Upgrades
---

### Post by .:Justus:. on 2009-03-24
Just hooked up a cd burner/drive to my netbook and was able to play music from a normal cd. The problem is, the drive doesn´t have an icon on the desktop and it isn´t in my file manager either.
I want to burn an iso to a blank cd, but to do so i have to tell my program where to burn the iso. And i don´t know where the drive is so i obviously don´t know where the blank cd is located either.
How can i make the drive appear on my desktop with an icon like my usb drives?

PS: when i type in lshw i can see it as this:

```
 *-cdrom
             description: SCSI CD-ROM
             product: WRR-52X
             vendor: ARTEC
             physical id: 0.0.0
             bus info: scsi@7:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrom1
             logical name: /dev/cdrw
             logical name: /dev/cdrw1
             logical name: /dev/scd0
             logical name: /dev/sr0
             version: 1.13
             serial: [ARTEC   WRR-52X         1.130
             capabilities: removable audio
             configuration: status=ready

```

Yet it isn´t listed in my fstab and i can´t mount it either!!!

---

### Post by avtolle on 2009-03-24
I believe it won't mount or be detected until you put a disk into the drive. That is what occurs with an external drive on my system.

---

### Post by .:Justus:. on 2009-03-24
> **avtolle said:**
> I believe it won't mount or be detected until you put a disk into the drive. That is what occurs with an external drive on my system.

Well as i said, i have a music cd inserted and it auto played as soon as i put it in. But the drive still doesn´t appear on my desktop or in my file manager!

---

### Post by avtolle on 2009-03-24
So I understand; the music CD autoplayed when inserted in said external drive, but an icon for it didn't appear on your desktop while the CD is playing? And, it didn't appear in the Places menu (again, while the cd is playing)? I'm no Xubuntu user, but IIRC, there should be an icon that appears on the XFCE desktop when an external device is detected/mounted.

---

### Post by .:Justus:. on 2009-03-24
it also tells me (in k3b) that there is no cd in the drive, eventhough there is....

---

### Post by .:Justus:. on 2009-03-24
> **avtolle said:**
> So I understand; the music CD autoplayed when inserted in said external drive, but an icon for it didn't appear on your desktop while the CD is playing? And, it didn't appear in the Places menu (again, while the cd is playing)? I'm no Xubuntu user, but IIRC, there should be an icon that appears on the XFCE desktop when an external device is detected/mounted.

Thats exactly whats happening, also(as stated in the post above this), its not recognizing my dvd +rw thats in the drive.

---

