---
title: "Privileges removed.  'Unlock' disabled"
date: 2008-10-12
forum: General Help
---

### Post by Euperia on 2008-10-12
I'm running Hardy 8.04 Desktop LTS on two machines (home and work) and keep them up to date via the Update Manager.

Recently I have noticed that I seem to have lost some admin privileges when doing things like plugging in a USB stick or trying to manage the network.

Administration > network displays the program but the 'Unlock' button is disabled.  Also, when I plug in any usb storage devices they are not auto-mounted.  

dmesg shows that the device has been recognised as sdc.

gnome-mount -vbd /dev/sdc1 shows:


```
** Message: Mount failed for /org/freedesktop/Hal/devices/volume_uuid_98F2_33C2
org.freedesktop.Hal.Device.PermissionDeniedByPolicy : org.freedesktop.hal.storage.mount-removable no <-- (action, result)

** (gnome-mount:8215): DEBUG: pk_action='org.freedesktop.hal.storage.mount-removable' pk_result='no'
** (gnome-mount:8215): DEBUG: gained privilege = 0
```

This was all working fine a few days ago and its the same on both machines.  Has anything changed in a recent update that could have caused this?  Where do I look?

---

### Post by Euperia on 2008-10-12
Additionally, If I try to change anything in System > Administration > Authorisations, any of the 'Grant' buttons are also disabled.

---

