---
title: "Myspace doesn't let me upload pictures when under Ubuntu..."
date: 2008-09-15
forum: General Help
---

### Post by Moonfrost on 2008-09-15
I have tried countless browsers and both different options on myspace to upload pictures but it never works if I'm using Linux, tried using Windows and it works no problem. I'm just trying to upload some pictures of a concert I went to and since I was the one with the camera myspace is always the easiest way to share it with my friends who also went.

Anybody know if the myspace picture uploader thing is OS specific by any chance?

---

### Post by y-lee on 2008-09-15
> Anybody know if the myspace picture uploader thing is OS specific by any chance?

No it works fine with linux. Just tested it myself using firefox to be sure it still works. I used the flash loader, the default. No problems. One day, months ago, I did have problems but it was temporary, I kept getting a myspace technical error message. Try it again and btw what version of flash are you using? And do you get any myspace errors if and when it doesn't work? And if it doesn't work have you tried opening firefox in a terminal and seeing if firefox gives any errors?

---

### Post by Moonfrost on 2008-09-15
> **y-lee said:**
> No it works fine with linux. Just tested it myself using firefox to be sure it still works. I used the flash loader, the default. No problems. One day, months ago, I did have problems but it was temporary, I kept getting a myspace technical error message. Try it again and btw what version of flash are you using? And do you get any myspace errors if and when it doesn't work? And if it doesn't work have you tried opening firefox in a terminal and seeing if firefox gives any errors?

I forgot to say that. No, myspace doesn't give me any errors, it just stays there like it's loading but nothing never happens. I once left an upload for 2 and a half hours to upload a small picture and it still said 0% no matter what I did, going to try opening Firefox on a terminal.

EDIT: This is what comes out when I try to upload something:
```

moonfrost@moonfrost-desktop:~$ firefox
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)

(npviewer.bin:7751): Gtk-CRITICAL **: gtk_style_detach: assertion `style->attach_count > 0' failed

(npviewer.bin:7751): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7751): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7751): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7751): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7751): Gtk-CRITICAL **: gtk_widget_destroy: assertion `GTK_IS_WIDGET (widget)' failed

(npviewer.bin:7775): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/filesystems/libgio.so: wrong ELF class: ELFCLASS64

(npviewer.bin:7775): Gtk-WARNING **: Error loading theme icon 'gtk-find' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(npviewer.bin:7775): Gtk-WARNING **: Error loading theme icon 'gtk-file' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(npviewer.bin:7775): Gtk-WARNING **: Error loading theme icon 'gtk-find' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(npviewer.bin:7775): Gtk-WARNING **: Error loading theme icon 'gtk-file' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(npviewer.bin:7775): Gtk-WARNING **: Error loading theme icon 'gtk-edit' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(npviewer.bin:7775): Gtk-WARNING **: Error loading theme icon 'gtk-add' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(npviewer.bin:7775): Gtk-WARNING **: Error loading theme icon 'gtk-remove' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(npviewer.bin:7775): Gtk-WARNING **: Error loading theme icon 'gtk-directory' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(npviewer.bin:7775): Gtk-WARNING **: Error loading theme icon 'gtk-add' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64

(npviewer.bin:7775): Gtk-WARNING **: Error loading theme icon 'gtk-remove' for stock: Unable to load image-loading module: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so: wrong ELF class: ELFCLASS64
```

EDIT #2: Just tried the non-HTML version of the uploader and it worked (it never had before either) so yeah.

---

### Post by thebrandon on 2008-09-15
I have the same problem not only with the myspace flash uploader but also with photobucket and especially with filesavr, which is the worst because it only has a flash uploader so I can not currently use my account!  Could this be because I am using SwiftFox?  I dont think so because I also have problems with Konqueror.

---

