---
title: "Strange MP3 player behavior"
date: 2013-10-15
forum: Hardware
---

### Post by Gannin on 2013-10-15
I have an older Philips MP3 player.  In past versions of Ubuntu and Lubuntu (12.10 and earlier) plugging the MP3 player in created a mount point in /media/user/mp3player and it would act just like a normal storage device in the file manager.

Now I'm using Lubuntu 13.04.  This is the first time I've plugged in this MP3 player since upgrading to Lubuntu 13.04.  When I plug it in, it no longer is mounted in /media/user and in the file manager it shows up as two devices:  One called MTP and one with the actual product name of the device.  Selecting either device shows mtp://[usb:001,006]/ in the file manager's location, along with a single item called Internal Storage.  If I click on that, the location changes to mtp://[usb:001,006]/65537 but then I get an endless busy cursor and nothing comes up.

This used to work just fine.  Why does it work differently now?

---

### Post by Yellow Pasque on 2013-10-16
It's possible that L/Ubuntu has switched to default MTP mode if the device is set to Auto and lets the OS decide. If you don't care for it, then see if you can change your player to use USB mode.

---

### Post by Gannin on 2013-10-16
I checked the settings on the MP3 player and it was indeed set to MTP.  So, I changed it to MSC, but now when I plug it in I get an error window that pops up saying Unable to open MTP device '[usb:001,006]'.  So it would appear MSC mode doesn't work either.

---

### Post by Yellow Pasque on 2013-10-17
It sounds like something (udev, fuse?) remembers the device as MTP and is still trying to access it that way.

---

