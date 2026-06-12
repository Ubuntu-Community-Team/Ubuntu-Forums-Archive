---
title: "CD drive does not exist"
date: 2005-11-25
forum: General Help
---

### Post by lerrup on 2005-11-25
Well, it does, but the mount point seems very confused.

Previously, it has always been media: /cdrom or /cdrom0 both of which are still mount points in file structure.

However, now when a disc is inserted I get the error message that media :/hdc does not exist.

I have recently updated to 3.5 rc1 and wonder if that has somehow screwed it up (but how?).  Does anyone know what the problem is and do we know what to do with this?

This is actually getting weirder as DVDs don't show up and neither Kaffeine or Totem seem to know they are there. But inspite of getting an error message KsCD is still able to play the CD.

It still isn't appearing as a drive, even when playing.

---

### Post by daller on 2005-11-28
[QUOTE=lerrup]Well, it does, but the mount point seems very confused.

Previously, it has always been media: /cdrom or /cdrom0 both of which are still mount points in file structure.

However, now when a disc is inserted I get the error message that media :/hdc does not exist.

I have recently updated to 3.5 rc1 and wonder if that has somehow screwed it up (but how?).  Does anyone know what the problem is and do we know what to do with this?

This is actually getting weirder as DVDs don't show up and neither Kaffeine or Totem seem to know they are there. But inspite of getting an error message KsCD is still able to play the CD.

It still isn't appearing as a drive, even when playing.[/QUOTE]

Can you access the disc through "/media/cdrom" ??? (/media/cdrom0)

The "media:"-thing is a new KDE3.5 improvement, but it is still buggy!

---

