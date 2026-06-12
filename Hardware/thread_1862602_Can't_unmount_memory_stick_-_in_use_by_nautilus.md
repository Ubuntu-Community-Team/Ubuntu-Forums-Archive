---
title: "Can't unmount memory stick - in use by nautilus"
date: 2011-10-16
forum: Hardware
---

### Post by jktrigg on 2011-10-16
Having just upgraded my wife's Pavilion laptop from 10.10 to 11.04, I reinstalled the driver for the jMicron card reader so she could transfer photos from our camera (missing cable).  It mounted the MS fine, and copied the files, but when we went to unmount it we got told that it was in use by Nautilus.  We had closed all file browser windows and right-clicked on the device on the desktop to remove it; we also tried right-clicking on the device in the Places menu.

---

### Post by FrederickSmith on 2011-10-17
[LEFT][COLOR=#333333][FONT=Helvetica Neue]By using Ubuntu, when you "eject" a USB stick from within Nautilus, the device actually disappears from the system. I'm not sure why this is, but neither Nautilus nor the command line can get it back. I guess the logic is that once you eject a USB stick you don't want it back, but are going to disconnect it.
The way I work around this (when needed), is by using **umount** instead of Nautilus. You could also just call **sync **to flush the filesystem buffers to the disk.

[Solution --> When Nautilus will not work/start on Fedora]("http://www.techyv.com/questions/nautilus-not-started-fedora")

So basically either a) Rebuild nautilus from source without that patch (and keep it up to date when you update your system...) or b) use another file manager (at least when unmounting ^^).
[/FONT][/COLOR][/LEFT]

---

