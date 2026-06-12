---
title: "Trouble mounting usb drives"
date: 2008-11-13
forum: General Help
---

### Post by SteinbergerNate on 2008-11-13
Recently, I have stopped being able to mount usb drives. I was able to 2 days ago but now nothing. The removable media shows up on my desktop and in Thunar but if I try to click and access the media it says this:

```
Failed to mount "Memory Stick Drive"
org.freedesktop.hal.storage.mount-removable no <-- (action, result).
```

If I right click it and say "Eject Volume" I get:

```
Failed to eject "Memory Stick Drive".
org.freedesktop.hal.storage.eject no <-- (privilege, result).
```

So it seems to be a permissions problem but I don't know where to go to fix it. I JUST had a permissions problem with my audio device and so I added my user name to the audio line in /etc/group but I can't figure out if that's what I need to do here.

I haven't tried from the command line because I can't figure out what device this is showing up as in /dev.

Edit: I KNOW it's a permissions problem now because I just ran Thunar as root and it let me mount the drive. I went back to Thunar as a regular user and the drive was still mounted. My regular user has no permissions to mount or eject usb drives.

---

### Post by vpablos on 2011-04-04
Hi there,

this is a rather old thread, but I have found the same problem, so I'll explain how I've fixed it:

unmount-others-no <-- (privilege, result)

in xfce4 is caused by halevt, so just uninstall it.

Deactivate in 
Menu > Settings > XFCE4 Settings Manager > Removable Drives and Media > Storage
all optional checkboxes in "Removable Storage"

Now you have to double-click to mount, but the problem has gone.

If when you mount (by double-click) you're not the device owner, take a look here to fix it:
[https://bbs.archlinux.org/viewtopic.php?pid=663160](https://bbs.archlinux.org/viewtopic.php?pid=663160)

---

