---
title: "xsane making me insane"
date: 2010-03-07
forum: Hardware
---

### Post by rogerdw on 2010-03-07
I am running 9.10 on HP  pavilion dv9000 with an HP Photosmart C3135 printer/scanner. I am having no luck with the scanning which used to work fine, now nothing is showing up. I get the following message when I run xsane in a terminal, but don't know what it means.

(xsane:3997): Gtk-WARNING **: GtkSpinButton: setting an adjustment with non-zero page size is deprecated


Any help greatly appreciated.

Thanks

---

### Post by rogerdw on 2010-03-08
Figured it out. I deleted the files xsane.mdf and xsane.rc in .sane/xsane and restarted the program and everything appears to be working.

Thanks

---

