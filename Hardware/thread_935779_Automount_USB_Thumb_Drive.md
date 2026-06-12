---
title: "Automount USB Thumb Drive"
date: 2008-10-02
forum: Hardware
---

### Post by DapperMe17 on 2008-10-02
Xubuntu Hardy

Hi, I'd like to have a USB Thumb Drive auto-mount at startup.

Currently, Hardy "sees" the drive just fine & a manual-mount works perfect.

The "mtab" file shows the mounted drive fine. 

However, there is nothing in "fstab" for this drive. (I know there needs to be!) 

The drive is FAT32 formatted.

Could someone offer an example of what I would need to add to my "fstab", so that the drive automounts & can be written to?

---

### Post by vanadium on 2008-10-02
Removable drives usually do not go into /etc/fstab. I suspect that xubuntu also will have automatic mounting mechanisms. If not, you indeed will need to add a line. a line for your USB would at the minimum look like

<devicename> <mount point> vfat defaults 0 0

see "man mount" for options (including fat specific options) that you can include.

---

### Post by DapperMe17 on 2008-10-03
Maybe I should have said..."permissions" :popcorn:

Yeah, no problem at all when manual mounting with the "right-click" option. 

However, because "Grsync" is keeping an exact match of everything going on in an internal FAT drive-to-USB external, it would be nice to have that USB drive auto-mount.

Unless....there is a GUI software, or system setting, that would accomplish this?

---

