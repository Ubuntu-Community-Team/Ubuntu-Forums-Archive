---
title: "? on mounting cdrom"
date: 2007-06-08
forum: Hardware &amp; Laptops
---

### Post by eroica on 2007-06-08
hello,
 i was trying to get rhythmbox to be my default player when i ran in to several questions. first i dont see anywhere to change file associations in gnome. then i thought i would put my audio cd in and goto nautilus select a song and right click "open with". alas i dont see anything listed under /media/cdrom or cdrom0. i tried putting an entry into fstab-"/dev/hdc 	/media/cdrom	auto	ro,user,noauto 	0	0" and then tried mount command but get error message " mount /dev/hdc /media/cdrom
mount: block device /dev/hdc is write-protected, mounting read-only
mount: you must specify the filesystem type"
 coming from Mandriva this always worked. Could anybody shed some light on how the mounting process is done in ubuntu & also how would one go about changing default music player in gnome.
thanx...

---

### Post by eroica on 2007-06-12
I guess I should have RTFM b4 asking that ? In case anybody else ran into this u should start Control Center>Other>Removable Drives & Media Prefs>Multimedia Tab.  U then must logoff for change to take effect. I would still be interested in knowing how fstab fits into Ubuntu if anyone has the answer. It's strange that when CD is playing I cant go into Nautilus and browse the CD in /media/cdrom like I can in KDE w/Konqueror on Mandriva...

---

