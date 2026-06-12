---
title: "Help with CD-R/DVD drive"
date: 2004-11-23
forum: Hardware &amp; Laptops
---

### Post by BugsyMalone on 2004-11-23
I have two nagging problems with the installation. I'll cover the first one here. I've got a Sony CD-RW CRX320E CD/DVD-ROM combo drive, and the drive plays music CD's fine, but when I'm having no luck getting it to play a DVD. I've installed the libdvdcss2 package, and tried to play DVD's in MPlayer, Totem, and gxine.  I get variations of the same error. The last one said: xine engine failed to start. No input plugin found. Maybe the file failed to exist, has wrong permissions or URL syntax error.  Read error from: /dev/dvd.

I don't know what this means. Any suggestions or ideas on what I can do?

---

### Post by scoon on 2004-11-25
[QUOTE=BugsyMalone]I have two nagging problems with the installation. I'll cover the first one here. I've got a Sony CD-RW CRX320E CD/DVD-ROM combo drive, and the drive plays music CD's fine, but when I'm having no luck getting it to play a DVD. I've installed the libdvdcss2 package, and tried to play DVD's in MPlayer, Totem, and gxine.  I get variations of the same error. The last one said: xine engine failed to start. No input plugin found. Maybe the file failed to exist, has wrong permissions or URL syntax error.  Read error from: /dev/dvd.

I don't know what this means. Any suggestions or ideas on what I can do?[/QUOTE]

Hey there, 

Make certain that you have a /dev/dvd.  libdvdcss2 likes to have that around.  If you do not have it then sudo ln -s /dev/cdrom-path /dev/dvd, once that symbolic link is created, then you should be able to get your dvd's playing.

scoon

---

