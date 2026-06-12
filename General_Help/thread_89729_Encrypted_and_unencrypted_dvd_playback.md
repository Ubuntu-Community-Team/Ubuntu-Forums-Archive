---
title: "Encrypted and unencrypted dvd playback"
date: 2005-11-13
forum: General Help
---

### Post by cbudden on 2005-11-13
Hello.

I have started to have a problem with playing back dvd's that are not encrypted.  If I have libdvdcss2 installed, then I can playback encrypted dvd's but if I try to play a unencrypted dvd Totem says it cannot play, have you got libdvdcss2 installed.  If I remove the lib then they work fine.

thanks

Edit

VLC works fine with both encrypted and unencrypted dvd's with libdvdcss2 installed.

Another edit

If I open the dvd in Totem by doing , File -> open location and type /media/cdrom0 the DVD plays fine.

Arrgh what is wrong !!  It worked LAST WEEK.

---

### Post by cbudden on 2005-11-13
Anyone?
This is what I get when i run totem from a terminal:
```


(totem:9104): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed

(totem:9104): Gtk-CRITICAL **: gtk_accel_label_set_accel_closure: assertion `gtk_accel_group_from_accel_closure (accel_closure) != NULL' failed
libdvdnav: Using dvdnav version 1.0.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Could not open /dev/hdc with libdvdcss.
libdvdread: Can't open /dev/hdc for reading
libdvdnav: vm: faild to open/read the DVD
libdvdnav: Using dvdnav version 1.0.1 from http://xine.sf.net
libdvdread: Using libdvdcss version 1.2.8 for DVD access
libdvdread: Could not open /dev/hdc with libdvdcss.
libdvdread: Can't open /dev/hdc for reading
libdvdnav: vm: faild to open/read the DVD

```

---

### Post by cbudden on 2005-11-14
Anyone?

---

