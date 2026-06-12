---
title: "Auto unmounting CD's"
date: 2009-10-27
forum: Hardware
---

### Post by dulek on 2009-10-27
After upgrading to 9.10, I'm getting problems with CD's. Finally I found a solution to make CD mount automatically, but after removing it from the drive, it doesn't unmount automatically and if I want next CD to mount correctly I need to do this manually.

fstab entry:
```
/dev/sr0        /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```

Any ideas? Which daemon is doing this?

---

### Post by phillw on 2009-10-27
The topic of auto-maounting is subject to some late ammendments ..

[https://bugs.launchpad.net/ubuntu/+bug/451668](https://bugs.launchpad.net/ubuntu/+bug/451668)

amongst others..

Running RIGHT up to the RC release date 

All the occurances of 'funnies' with automount seem to have been signed off as resolved, albeit very recently -  Have you got the latest RC of 9.10 ?

Regards,

Phill.

---

### Post by dulek on 2009-10-27
I've got any recent updates. I have discovered that gnome-volume-manager isn't running on my system. Command
```
/usr/lib/gnome-volume-manager/gnome-volume-manager -n
```
returns
```
manager.c/686: setting[0]: string: filemanager = nautilus -n --no-desktop %m
manager.c/691: setting[1]: bool: autophoto = 0
manager.c/686: setting[2]: string: autophoto_command = f-spot-import
manager.c/691: setting[3]: bool: autovideocam = 0
manager.c/686: setting[4]: string: autovideocam_command = 
manager.c/691: setting[5]: bool: autowebcam = 0
manager.c/686: setting[6]: string: autowebcam_command = cheese --hal-device=%h
manager.c/691: setting[7]: bool: autopalmsync = 0
manager.c/686: setting[8]: string: autopalmsync_command = gpilotd-control-applet
manager.c/691: setting[9]: bool: autopocketpc = 0
manager.c/686: setting[10]: string: autopocketpc_command = multisync
manager.c/691: setting[11]: bool: autoprinter = 0
manager.c/686: setting[12]: string: autoprinter_command = 
manager.c/691: setting[13]: bool: autoscanner = 0
manager.c/686: setting[14]: string: autoscanner_command = xsane
manager.c/691: setting[15]: bool: autokeyboard = 0
manager.c/686: setting[16]: string: autokeyboard_command = 
manager.c/691: setting[17]: bool: automouse = 0
manager.c/686: setting[18]: string: automouse_command = 
manager.c/691: setting[19]: bool: autotablet = 0
manager.c/686: setting[20]: string: autotablet_command = 
manager.c/700: settings[21]: float: percent_threshold = 0,050000
manager.c/700: settings[22]: float: percent_used = 0,010000
manager.c/665: daemon exit: live and let die

```

This is because my options in gnome-volume-properties are all off. But there are no option for CD-s (they are in gconf, but not working). If gnome-volume-manager isn't responsible for automount - what is? Maybe I turned it off?

---

### Post by dulek on 2009-10-27
Ok, I've got it - I installed pmount and removed fstab entry and automount is working for CD-rom. But I have problem with mounting hard drives. Could someone show fstab automatically created by Karmic? I want to look on NTFS drive entries.

---

