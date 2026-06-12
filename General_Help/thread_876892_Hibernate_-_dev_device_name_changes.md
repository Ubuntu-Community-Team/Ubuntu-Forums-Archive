---
title: "Hibernate - /dev/ device name changes"
date: 2008-08-01
forum: General Help
---

### Post by Rod Hull on 2008-08-01
Following on from my [previous thread](http://ubuntuforums.org/showthread.php?p=5489215) that got little attention, I thought I'd start a new one.

Basically, after waking up from hibernation, any external USB device that was plugged in and mounted when the machine was hibernated, has its /dev/ name changed, and as such its mountpoint altered, but the old mountpoint remains but is then inaccessible.

e.g. If my external USB HD is originally /dev/sdd and mounted at /media/disk having booted from cold, then after hibernation it changes to /dev/sde and is automounted at /media/disk-1 but /media/disk remains but is inaccessible. This happens each subsequent time the machine is hibernated/woken, with an increment in the letter at /dev/sd? and a increment in number at /media/disk-?

This is INCREDIBLY annoying, and I've found no way of stopping it (adding usb_storage to MODULES_WHITELIST= of /etc/defaults/acpi-support does nothing). 

Waking from hibernation should return the machine to the exact same state as before - this is not the case here...it wouldn't matter if as a workaround I could add the external USB drive into fstab so it's mounted permanently, but since the device is USB, its name itself in /dev/ changes too, this is useless...

---

### Post by caljohnsmith on 2008-08-01
You might be able to find a workaround, but that definitely sounds like a bug anyway. If I were you I would report it at bugs.launchpad.net and they can probably help you resolve it.

---

### Post by Rod Hull on 2008-08-03
So, I discovered that hibernation is performed by pm-utils. I found another thread that mentioned a similar problem with suspend, and not hibernation. It turns out that a fix can be easily achieved to this with the following:

Create a simple script (I called it 66mount_fix) and put it in /etc/pm/sleep.d containing something like the following:

```

#!/bin/bash
case $1 in
    hibernate)
        umount /media/disk*
        ;;
    suspend)
        ;;
    thaw)
        ;;
    resume)
        mount /media/disk
        ;;
esac

```

This seems to do the trick just fine.

---

