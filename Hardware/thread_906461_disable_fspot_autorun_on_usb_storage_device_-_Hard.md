---
title: "disable fspot autorun on usb storage device - Hardy"
date: 2008-08-31
forum: Hardware
---

### Post by PlancksCnst on 2008-08-31
I have a microsd card that I periodically load up with podcasts.  There are also some images on it.  The system used to prompt me with a dialog asking what action I'd like to take.  I must have accidentally chosen f-spot once and now every time I put in the card, f-spot starts.

I have looked in the "Removable Drives and Media Preferences" app and the option for "Import... when connected" under the digital camera is not checked. There is no setting for generic removable drives.

How can I fix this?

---

### Post by IntuitiveNipple on 2008-08-31
Open a Nautilus file-system browser window (Places > Home Folder). Follow Edit > Preferences > Media. Look at the setting for the "Photos" entry.

---

### Post by PlancksCnst on 2008-09-02
Thanks. That worked.  I consider that a bug. There should not be two places to change settings that handle the same functionality.

---

### Post by IntuitiveNipple on 2008-09-02
It isn't. They are two subtly different things.

System > Preferences > Removable Drives and Media, "Digital Camera" controls gnome volume_manager via gconf:

/desktop/gnome/volume_manager/

which triggers external programs based on udev events. In the default case it runs f-spot-import to copy files from the device.

Nautilus, via its Edit > Preferences > Media settings determines the nautilus action only. By default it will ask, but the user can set a number of actions. Any installed program that has registered with the system to handle the mime-type **x-content/image-dcf** is listed in the "Photos" drop-down list.

The mime-types that shouldn't be handled by the system-registered handler are in the gconf keys:

/apps/nautilus/preferences/media_autorun_x_content_ask
/apps/nautilus/preferences/media_autorun_x_content_ignore
/apps/nautilus/preferences/media_autorun_x_content_open_folder

In the case of the user choosing to always use f-spot, Nautilus will have f-spot *open the folder*.

Note that is different from the system preference to import digital camera files, when f-spot-import is executed.

I agree the two are confusingly similar though :)

---

### Post by PlancksCnst on 2008-09-04
Okay, are you saying, udev deals with the device mount event, and Nautilus deals with the directory open event?  If this is the case, then udev should always activate Nautilus (devices are abstracted as directories, after all), and let Nautilus deal with the behavior.

I am not convinced that it is not a bug. Why have (by default) two things that do the same basic functionality? It would be like having Totem and VLC both installed by default.

---

