---
title: "[SOLVED] change mount point of an unmounted device"
date: 2008-08-29
forum: General Help
---

### Post by mpgarate on 2008-08-29
I tried to change the mount point of my ipod, and failed. When i connect it I receive an error saying > unable to mount volume.
mount_point cannot contain the following characters: newline, G_DIR_SEPERATOR,usually /

can someone please help?

edit: solved by

running gconf-editor

deleting my entry for /system/storage/drives/_org_freedesktop_Hal_devices_voume_uuid_*/mount_point

(or something close to that name)

then i ejected and mounted

---

