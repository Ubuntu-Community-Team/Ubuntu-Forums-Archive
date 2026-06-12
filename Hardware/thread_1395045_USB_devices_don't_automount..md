---
title: "USB devices don't automount."
date: 2010-01-31
forum: Hardware
---

### Post by Roanoke on 2010-01-31
I can't automount any usb memory devices. I must become root in a terminal and then mount them. This is highly inconvenient. When I connect a usb device to my computer, the light on the device flashes a few times, then stops.

---

### Post by Barriehie on 2010-01-31
Somewhat the same issue here.  I found that of two different brands of USB memory sticks one will automount and the other one had to have an entry in /etc/fstab to mount.  The PNY/Attache one will automount while the HP requires the fstab entry.

The entry in my /etc/fstab:
```

/dev/sdc1   /media/disk auto auto,user,rw,sync  0       0

```

Your /dev/xxxx and mountpoints may/can be different if you try this method.
What I would do/did is mount the device via nautilus and then viewed the properties to see the /dev/xxxx and create a mount point somewhere and add to /etc/fstab.

HTH,
Barrie

---

### Post by Roanoke on 2010-01-31
> **Barriehie said:**
> 
What I would do/did is mount the device via nautilus and then viewed the properties to see the /dev/xxxx and create a mount point somewhere and add to /etc/fstab.


How could I mount it via nautilus? Devices can only be mounted via the shell, iirc. Also, adding each device that I might want to connect to fstab is a bastardization, not a solution. It's like saying to a person with a broken leg, "Oh, but if you use a stick and hop on one foot it doesn't hurt."

---

### Post by Barriehie on 2010-01-31
I have 2 devices and it worked for me.  Also, per my post about the different vendors obviously all USB devices are not the same hence the system doesn't treat them all the same way.

---

### Post by Roanoke on 2010-01-31
Yes, but it worked fine before. Every device I plugged in was recognized. USB devices are, internally, the same. Two contacts for power, two for data, and the computer needs to understand what kind of device it is, and the device tells the computer what it is.

---

