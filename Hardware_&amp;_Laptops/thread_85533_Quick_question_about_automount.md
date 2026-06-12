---
title: "Quick question about automount"
date: 2005-11-02
forum: Hardware &amp; Laptops
---

### Post by ionophore on 2005-11-02
Hey everyone, i have just a quick question about automount... how do i disable it?  I'd like to mount things like cd's and dvd's manually via the command line.  None of this autodetection business.  

That said, i'd like to keep the ability to automount installed... is there just a config file somewhere that i can edit to specifically tell the eystem not to automatically mount CD's and DVD's?

Thanks,

-ben

---

### Post by az on 2005-11-02
System - Preferences - Removable drives and Media

And automount is a different thing.  Ubuntu uses Gnome-volume-manager, and kubuntu uses another deamon (for which I forget the name)  Automount is a kernel module and some userspace tools:

(autofs: "Autofs controls the operation of the automount daemons. The
 automount daemons automatically mount filesystems when they
 are used and unmount them after a period of inactivity. This
 is done based on a set of pre-configured maps.")


So basically, with autofs, you define the mountpoint and then when any application asks the kernel to look there, it tries to mount the media.  If you set a five second interval, for example, the media will remain mounted for five seconds after the last time it was sought.  Basically, you can read a file from a cd and press eject and expect it to eject, since it is not mounted anymore.  Anyway, it is stable, but caused problem when KDE, Gnome and other desktop environments try to do the same thing.  So, it is no longer used.

---

### Post by ionophore on 2005-11-02
hey thanks for the reply.  Not exactly what i was expecting, but it will do :)

cheers,

-ben

---

### Post by Schmots on 2005-11-02
/etc/fstab..
find the line about your cdrom drives.. and add noauto to the section of options

---

### Post by az on 2005-11-02
[QUOTE=Schmots]/etc/fstab..
find the line about your cdrom drives.. and add noauto to the section of options[/QUOTE]
Actually, that will only prevent them from mounting on boot, if there is something in the cdrom drive, for example.

ionophore,as I said, go toSystem - Preferences - Removable drives and Media to set your gvm settings.

---

