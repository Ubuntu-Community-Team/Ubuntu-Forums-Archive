---
title: "HAL + USB devices"
date: 2008-12-24
forum: Hardware
---

### Post by msamson on 2008-12-24
Please See : [http://ubuntuforums.org/showthread.php?t=1019944]("http://ubuntuforums.org/showthread.php?t=1019944")


I would like not to make a duplicate but I feel General Help might not be able to help on this case.

What I am trying to do is to mount any usb device with a filesystem (usb disks, hard drives, cameras) to one location instead of using the volume name in /media.

Let suppose the following:
The unit (computer) only has 1 accessible usb port. No more than 1 device might  be plugged at the same time (ok, usb hub exists, but let suppose they don't)

Once the device is plugged and mounted, an executable has to be called.

Gnome is not installed. (or may be, but we must not rely on gnome-volume-manager or any automount in gnome)

--

I know HAL is able to "specify" a mount point for a device type or specific device. It is also able to launch executables in response to events (plug, unplug, etc.)

Any ideas on how to achieve this?

I cannot use the same volume name as the usb devices plugged in the unit will not be mine.

---

### Post by msamson on 2008-12-24
First half of the solution has been found:

```

<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<deviceinfo version="0.2">
 <device>
   <match key="block.is_volume" bool="true">
     <match key="@block.storage_device:storage.hotpluggable" bool="true">
       <merge key="volume.policy.desired_mount_point"
type="string">guest</merge>
       <append key="info.callouts.add" type="strlist">beep -f 77</append>
     </match>
   </match>
 </device>
</deviceinfo> 
```

If a mod see this thread, might consider closing it as it will become a duplicate.

EDIT: Updated the code block, solution inside :D

---

