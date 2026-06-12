---
title: "usb automount and gnome-mount"
date: 2008-11-26
forum: General Help
---

### Post by dafi on 2008-11-26
Under Ubuntu 8.10 the automount feature doesn't work.

If I try to manually mount device all works fine.

If I do the following command to my usb harddisk formatted in NTFS

gnome-mount -vbd /dev/sdf1

I receive

```
** (gnome-mount:9799): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_C60CBC2E0CBC1AFF
** (gnome-mount:9799): DEBUG: read default option 'locale=' from gconf strlist key /system/storage/default_options/ntfs-3g/mount_options
** (gnome-mount:9799): DEBUG: read default option 'exec' from gconf strlist key /system/storage/default_options/ntfs-3g/mount_options
** (gnome-mount:9799): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_C60CBC2E0CBC1AFF with mount_point='DAFI', fstype='ntfs-3g', num_options=2
** (gnome-mount:9799): DEBUG:   option='locale=it_IT.UTF-8'
** (gnome-mount:9799): DEBUG:   option='exec'
Montato /dev/sdf1 su "/media/DAFI"

```

and nautilus opens automatically.

and when I mount with gnome-mount my cell phone I receive

```
gnome-mount 0.8
** (gnome-mount:9929): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_1BE6_F1DD
** (gnome-mount:9929): DEBUG: read default option 'shortname=mixed' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:9929): DEBUG: read default option 'uid=' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:9929): DEBUG: read default option 'utf8' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:9929): DEBUG: read default option 'umask=077' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:9929): DEBUG: read default option 'exec' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:9929): DEBUG: read default option 'flush' from gconf strlist key /system/storage/default_options/vfat/mount_options
** (gnome-mount:9929): DEBUG: Mounting /org/freedesktop/Hal/devices/volume_uuid_1BE6_F1DD with mount_point='Dafi', fstype='', num_options=6
** (gnome-mount:9929): DEBUG:   option='shortname=mixed'
** (gnome-mount:9929): DEBUG:   option='uid=1000'
** (gnome-mount:9929): DEBUG:   option='utf8'
** (gnome-mount:9929): DEBUG:   option='umask=077'
** (gnome-mount:9929): DEBUG:   option='exec'
** (gnome-mount:9929): DEBUG:   option='flush'
Montato /dev/sdf1 su "/media/Dafi"

```

How can I restore the automount?

Consider that under Ubuntu 7.10 both HD and cellphone are automounted without problems

---

### Post by dafi on 2008-12-09
Up

From Intrepix CD Live all works fine.

I've tried to compare files in live /etc adn my system but I was unable to find important differences.

I've dumped the content of gconftool (both live and my system) and after comparison I was unable to find important differences.

From polkit-gnome-authorization all seems correct (org.freedesktop.hal.storage.mount-removable key)

I feel like a Windows user with strange behaviors after an upgrade :mad:

---

### Post by joshua1983 on 2008-12-15
What size is the usb key?... I have a 1Gb usb key and automount normally, but with my 4Gb usb key I must mount manually... why??
thanks

---

