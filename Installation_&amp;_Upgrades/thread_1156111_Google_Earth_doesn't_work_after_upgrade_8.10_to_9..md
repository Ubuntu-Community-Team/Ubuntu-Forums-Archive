---
title: "Google Earth doesn't work after upgrade 8.10 to 9.04 64-bit"
date: 2009-05-11
forum: Installation &amp; Upgrades
---

### Post by Milleman on 2009-05-11
Hi there!

Just upgraded my 64-bit 8.10 to 9.04. Seems to work fine. Except for Google Earth, which now can't reach the map server. I then downloaded the latest G-Earth for Linux and then tried to reinstall it by starting the install binary from the text terminal. The installation went through, but I received the following messages at the terminal:

```

~$ ./GoogleEarthLinux.bin
Verifying archive integrity... All good.
Uncompressing Google Earth for GNU/Linux 5.0.11733.9347..............................................................
Gtk-Message: Failed to load module "canberra-gtk-module": /usr/lib/gtk-2.0/modules/libcanberra-gtk-module.so: wrong ELF class: ELFCLASS64
loki_setup: Suspect size value for option option

/usr/lib/gio/modules/libgioremote-volume-monitor.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgioremote-volume-monitor.so
/usr/lib/gio/modules/libgiogconf.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgiogconf.so
/usr/lib/gio/modules/libgvfsdbus.so: wrong ELF class: ELFCLASS64
Failed to load module: /usr/lib/gio/modules/libgvfsdbus.so
loki_setup: Suspect size value for option option

Installing mimetypes...
Installing desktop menu entries...
Installing desktop icon...
~$

```

Is this anything serious? Is there something I can do?

Cheers!

---

### Post by Milleman on 2009-05-11
Okay...
Managed to make it work with help of the instructions from the following website:

[http://www.brighthub.com/computing/linux/articles/33340.aspx]("http://www.brighthub.com/computing/linux/articles/33340.aspx")

Now life's good again! :)

---

