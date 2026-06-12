---
title: "help!usb cdrom isn't recognized"
date: 2005-03-09
forum: Hardware &amp; Laptops
---

### Post by lorap on 2005-03-09
i've usb mouse working very good regardless what type of usb connection it is plugged in but the problem arises when i try to use my usb cdrom device.
i've installed from synapsis the program called "usbviewer" and run it several times.when the power on cdrom's off it recognezed it as being connected but unvaible, but once i turn on the power it sees it as correctly working device.
anyway, when i open "disks" folder the ubuntu doesn't recognise it so the only cdrom it shows is the regular one, i mean the internal one.
hope somebody'd help me to solve this problem cause i just can't quit using this device, it's important to me use it.this's the case why i still have windows installed on my pc.i remember windows at its first stages been having the same troubles.
thanks
pavel

---

### Post by bigzak on 2005-03-09
This should be quite a simple one. In the Device Manager see what SCSI device the external drive is emulating (it should be sr0 or sr1) and add that to your /etc/fstab like this:

/dev/sr0  /media/usb-cdrom  iso9660  defaults,noauto,user,rw  0  0

and make the /media/usb-cdrom directory. It should then appear in the Disks folder.

The reason for this is because the disks folder only contains disks in the /etc/fstab file that are marked as noauto.

As an extra, you could add a udev rule to automatically create a /dev/usb-cdrom symlink when you plug it in so that you don't need to know which device node has been created for it.

---

### Post by lorap on 2005-03-10
hi friend!
thank you very much you've found some time to help me.
i've been trying to solve this problem for a long time.
thank you again friend, i'll try your proposition once i get home and i'll let you know.
pavel

hi friend!
i've done everything as you've wriiten me.now,when open disks folder i can see usb-cdrom folder but it still popups an error message:

"Unable to mount the selected volume. The volume is probably in a format that cannot be mounted."

and when i open show more details i see there:

"mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       or too many mounted file systems"

it seems like it now works but there's a settings problem
thanks
pavel

---

### Post by lorap on 2005-03-10
hi friend!
i've done everything as you've wriiten me.now,when open disks folder i can see usb-cdrom folder but it still popups an error message:

"Unable to mount the selected volume. The volume is probably in a format that cannot be mounted."

and when i open show more details i see there:

"mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
or too many mounted file systems"

it seems like it now works but there's a settings problem

when i change from sr0 to sr1 i get this message:

"Unable to mount the volume. There is probably no media in the device."

and when i open show more details i see there:

"mount: /dev/sr1 is not a valid block device"

thanks
pavel

---

### Post by lorap on 2005-03-11
it did help me friend!
thank you very much!
pavel

---

