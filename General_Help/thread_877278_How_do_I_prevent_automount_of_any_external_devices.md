---
title: "How do I prevent automount of any external devices"
date: 2008-08-01
forum: General Help
---

### Post by bravespear on 2008-08-01
I'm trying to create a LiveCD (using Kubuntu Hardy) for my employer, and I need to know if there is a way to prevent the LiveCD from mounting any other devices (HDD, CD/DVD,USB drive, etc).  My employer requires this for security and liability purposes, and is just about the last bridge I need to cross before it is a viable solution.

Thanks!

---

### Post by derrick81787 on 2008-08-01
I'm not 100% sure if this will work, but I think you should remove some lines in your /etc/fstab. Removing the line with your cdrom device in it will keep it from auto-mounting (I think). However, if it's a LiveCD, you can't really use the cdrom for anything anyway...

As far as auto-mounting usb devices, I think there's a line in the default fstab that says something about usbfs.  I'm not 100% sure because I'm at work (on Windows) right now, but I think it's there.  I'd be willing to bet that removing that will prevent anything connected through usb from being mounted automatically.

I haven't tried any of this myself, though, so I can't tell you that it'll work for sure.  It can't hurt to make a backup of your /etc/fstab and give it a try, though.

Also, you can do this through the "Removable Drives and Media" preferences in GNOME, which makes it seem like there is a per user, no-root-access-needed way of doing this (even in KDE), but editing your /etc/fstab will be permanent and system-wide (which is probably what you want).

Let me know if this works for you.

- Derrick

---

### Post by derrick81787 on 2008-08-01
After re-reading your post, I think I mis-understood you.  Doing what I said will keep it from automatically mounting your cdrom/usb-drives, but you can still manually mount them.  I don't think there's a way to prevent manual mounting of drives.

Maybe someone else will a little more Linux knowledge will prove me wrong.

- Derrick

---

### Post by Vivaldi Gloria on 2008-08-01
> **bravespear said:**
> I'm trying to create a LiveCD (using Kubuntu Hardy) for my employer, and I need to know if there is a way to prevent the LiveCD from mounting any other devices (HDD, CD/DVD,USB drive, etc).  My employer requires this for security and liability purposes, and is just about the last bridge I need to cross before it is a viable solution.

Thanks!

It's udev which generates devices in /dev. Udev rules live in

/etc/udev/rules.d

You can change the rules to achieve whatever you want. Google udev and find some guides about it. Start with these:

[http://www.archive.org/details/HampshireLinuxUserGroup_udev](http://www.archive.org/details/HampshireLinuxUserGroup_udev)
[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)
[http://en.wikipedia.org/wiki/Udev](http://en.wikipedia.org/wiki/Udev)

---

### Post by bravespear on 2008-08-04
Thanks everyone for pointing me in the right direction!

---

### Post by geirha on 2008-08-04
Actually. Udev only creates device nodes in /dev. HAL, the hardware abstraction layer, listens to what udev is doing, and when udev finds a new device, HAL tries to figure out what type of device it is, and if it is a removable storage device, it notifies everyone listening that this should be mounted. gnome-volume-manager takes the ball and mounts it. 

You can find the configuration file for hal at: /etc/hal/fdi/policy/preferences.fdi
I tried adding some configuration that disables mounting of removable storage devices, and ran "sudo /etc/init.d/hal restart". After that it stopped mounting my USB-pendrive automatically.

Here's my configuration. The parts I added marked in bold. 
```

  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
[B]    <match key="storage.removable" bool="true">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
    </match>[/B]
  </device>

```

---

### Post by bravespear on 2008-08-04
> **geirha said:**
> Actually. Udev only creates device nodes in /dev. HAL, the hardware abstraction layer, listens to what udev is doing, and when udev finds a new device, HAL tries to figure out what type of device it is, and if it is a removable storage device, it notifies everyone listening that this should be mounted. gnome-volume-manager takes the ball and mounts it. 

You can find the configuration file for hal at: /etc/hal/fdi/policy/preferences.fdi
I tried adding some configuration that disables mounting of removable storage devices, and ran "sudo /etc/init.d/hal restart". After that it stopped mounting my USB-pendrive automatically.

Here's my configuration. The parts I added marked in bold. 
```

  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
[B]    <match key="storage.removable" bool="true">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
    </match>[/B]
  </device>

```

Thanks for the help! Is this also where I would configure the livecd to not mount the internal HDD as well?

---

### Post by geirha on 2008-08-05
I haven't checked the LiveCD, but I'm fairly certain it uses HAL too, so I would assume the same configuration applies.

---

