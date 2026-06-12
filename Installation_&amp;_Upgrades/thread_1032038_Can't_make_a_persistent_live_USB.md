---
title: "Can't make a persistent live USB"
date: 2009-01-05
forum: Installation &amp; Upgrades
---

### Post by Lunatico_22 on 2009-01-05
I bought a 2 GB Kingston DataTraveler 400 USB drive so I could use Ubuntu in other computers as a portable environment. I tried to install 64 bit intrepid on it with the extra space (1.2 GB) for documents and extra programs. In the first install, the installer hanged at 6 % and then failed to complete the install. Here is the log that the usb-creator generated:

-- Starting up at 22:09:50 --
[22:09:50] new device:
{'capacity': dbus.UInt64(1998742528L), 'uuid': 'B077-1DC4', 'label': 'FEDORA', 'free': 1999560704, 'fstype': 'vfat', 'device': '/dev/sdf1', 'mountpoint': '/media/FEDORA', 'udi': '/org/freedesktop/Hal/devices/volume_uuid_B077_1DC4'}
[22:09:50] adding: /dev/sdf1
[22:09:57] mounting /home/lunatico/Programas/OS/ubuntu-8.10-desktop-amd64.iso
[22:09:57] updating dest_status as part of update_row_state
[22:10:02] Installing...
[22:10:02] Source CD: /home/lunatico/Programas/OS/ubuntu-8.10-desktop-amd64.iso
[22:10:02] Destination disk: /dev/sdf1
[22:10:02] Persistence size: 1197 MB
[22:10:02] Marking partition 1 as active.
[22:10:02] installing the bootloader to /dev/sdf1.
[22:10:03] ['/usr/share/usb-creator/install.py', '-s', '/tmp/tmpSKz8Oy/.', '-t', '/media/FEDORA', '-p', '1197']
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/usbcreator/backend.py", line 202, in property_modified
    if dev.PropertyExists('volume.is_disc') and dev.GetProperty('volume.is_disc'):
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 68, in __call__
    return self._proxy_method(*args, **keywords)
  File "/var/lib/python-support/python2.5/dbus/proxies.py", line 140, in __call__
    **keywords)
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 607, in call_blocking
    message, timeout)
DBusException: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/volume_uuid_B077_1DC4
[22:10:08] removing /org/freedesktop/Hal/devices/volume_uuid_B077_1DC4
[22:10:08] deleting /dev/sdf1 from the ui
[22:10:08] device removed and none left.  source = False
ERROR:dbus.connection:Exception in handler for D-Bus signal:
Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/dbus/connection.py", line 214, in maybe_handle_message
    self._handler(*args, **kwargs)
  File "/usr/lib/python2.5/site-packages/usbcreator/backend.py", line 252, in device_removed
    gobject.source_remove(self.timeouts[d])
KeyError: '/dev/sdf1'
[22:10:08] Unmounting source volume.
[22:10:08] Install command exited with code: 256
[22:10:08] Forcing shutdown of the install process.
[22:10:08] Unmounting source volume.
[22:10:08] Install failed.

After many tries I came up with this:

-The installer finished with a FAT16 partition but it was unbootable, the bios says that there is not a Operating System on the pendrive
-The installer crashes with a FAT32 partition formated with gparted or fdisk
-The installer crashes with any non-FAT partition, when the "format" button appear at the usb-creator. Afther clicking it and going on with the installer, it crashes again at 6%
-The installer finished with a FAT32 partition formated in windows, but it is VERY slow (takes about 30 min. to finish), but it is not bootable, a "Boot Error" message appear on the screen while trying to boot with it

I've tried to install a new MBR and upgrade syslinux to the newest version with no success. I also tried with a Kingston 8GB Datatraveler 101 and got the same problems. At the end I tried to use the liveusb-creator of Fedora 10 to make a Fedora usb and also failed. 

A month ago I created a 1GB drive without problems, which I stopped using because its lack of space... I hope someone could help

---

### Post by dynathi on 2009-01-06
I had the same problem, but in my case it was because the CD was bad. Using an ISO instead solved my problem. However, it looks like you are already using an ISO... Perhaps it has something to do with this line:


DBusException: org.freedesktop.Hal.NoSuchDevice: No device with id /org/freedesktop/Hal/devices/volume_uuid_B077_1DC4

If you can still create one with the 1 GB drive, the 2 GB drive is probably a bad one, although you could try installing with another computer (this is what I would do).

Perhaps this is a stupid question, but have you marked the partition bootable under cfdisk or gparted? This could be the reason why it says "Operating system not found".

---

### Post by hyperdude111 on 2009-01-06
I have a similar but different problem, I can create a live usb with 5gb for persistant storage the final product is never persistant (i cant save my settings)

---

### Post by Pumalite on 2009-01-06
[http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman](http://ubuntuforums.org/showthread.php?t=789528&highlight=Herman)
[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

---

### Post by Lunatico_22 on 2009-01-07
Yes, I've marked the partition as bootable, still no luck.

I have tried also the liveUSB application that appear in the links from pumalite, which also failed to make the usb bootable... I'll try to install ubuntu directly to another drive, since this one seems to be a bad one.

Thanks for your advice :)

---

### Post by tbv on 2009-01-22
Hyperdude,
I am having exactly the same problem. Ubuntu works fine on the stick, but it is not persistant. Even I created the stick configuration via the USB creator in Ubuntu 8.10 itself and used an ISO. I would highly appreciate if you can let me know once you solved your problem. In the meantime, I will try it with an other external disc and see what will come out of that. Cheers, TBV

---

### Post by sugi007 on 2009-01-28
I had on and off problems with creating persistent and bootable Live Ubuntu 8.10 USB drives. So much so that I have created an entry about it on my blog with troubleshooting.

[http://www.codesingh.com/2009/01/ubuntu-on-stick-with-persistence.html]("http://www.codesingh.com/2009/01/ubuntu-on-stick-with-persistence.html")

Hope this solves your problem.

---

### Post by TrueLugia121 on 2009-05-01
what about that tutorial at pendrivelinux.com? doesn't that give the same issues?

---

