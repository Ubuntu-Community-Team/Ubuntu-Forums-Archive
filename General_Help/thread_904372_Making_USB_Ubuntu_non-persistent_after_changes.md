---
title: "Making USB Ubuntu non-persistent after changes"
date: 2008-08-29
forum: General Help
---

### Post by Bradleelee on 2008-08-29
Greetings all! I am very new to the community, and Ubuntu for that matter, so please bear with me. Hopefully my questions is in the right forum and if not I apologize.

In general, I am looking to load Ubuntu to a USB, be able to boot to it, make changes to the files on the USB (load programs, and files on it etc), and then make that USB drive non-persistent once I am done.

I have found many tutorials out there that do some of what I want and not others.  For instance, at this site there is a tutorial stating how to make a non-persistent install of Ubuntu.

[http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/](http://www.pendrivelinux.com/2008/04/09/usb-ubuntu-804-installation-from-windows/)

The problem here is that it will only keep what was originally on it from the zip files.  And then another tutorial here which states how to make a persistent USB boot of Ubuntu.

[http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/](http://www.pendrivelinux.com/2008/05/08/usb-ubuntu-804-persistent-install-tutorial/)

This is great since I can now load all of my programs and files on it that I want.  However, I have no idea how to make this non persistent once I have everything on it.  This seems like it would have a relatively "easy" solution since the previous non persistent install had programs and such loaded on it from the start as well.

Now what I do NOT want is to use a "persistent loop." In other words 250MB of the USB is persistent while the rest is non persistent.  I must be able to make all of it non persistent.

Any help would be greatly appreciated. I have been using your amazing advice for some time, but this is the first I have posted. Thank you all for the hard work!

---

### Post by Oldsoldier2003 on 2008-08-29
Removed this support request from the tutorials and tips moderation queue. A quick reminder to everyone that new threads in T&T are held for moderation, please post new support threads in the appropriate sub form.

---

### Post by sofamensch on 2008-08-29
As far as i know about this, you have yourself or automatically created the /etc/fstab file in that way, that it mounts the ubuntu cd iso as "loop", and you must have a second partition to hold all the changes etc.

Just mount the second partition as read only in fstab.

---

