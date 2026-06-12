---
title: "Firefox address bar not changing"
date: 2008-08-11
forum: General Help
---

### Post by blikkboks on 2008-08-11
I have had this really weird problem with Firefox lately. The problem is that when i enter a URL like Ubuntu.com it goes to Ubuntu's homepage but the address bar still shows Ubuntu.com. If i then enter something into the Google bar it showed what i searched for but the address bar i still showing Ubuntu.com. Really weird problem. Also the back and forward buttons are not working.

Pictures: 
[http://img521.imageshack.us/img521/6364/screenshotoe5.png]("http://img521.imageshack.us/img521/6364/screenshotoe5.png")
[http://img382.imageshack.us/img382/6300/screenshot1gl6.png]("http://img382.imageshack.us/img382/6300/screenshot1gl6.png")
[http://img382.imageshack.us/img382/6845/screenshot2ql7.png]("http://img382.imageshack.us/img382/6845/screenshot2ql7.png")
[http://img147.imageshack.us/img147/9527/screenshot3lw7.png]("http://img147.imageshack.us/img147/9527/screenshot3lw7.png")

Help!

---

### Post by blikkboks on 2008-08-11
Help! I am at the second page now! This is realy annoying the reload button does not work neither! This is realy annoying.

---

### Post by tarps87 on 2008-08-11
Have you tried reinstalling firefox. Its sounds like a file may have been corrupted

---

### Post by ajgreeny on 2008-08-11
Very weird!  Have you tried temporarily renaming your ~/.mozilla folder as ~/.mozillaold and then restarting FF.  You won't have all your personal setup for it but at least you will be able to check that the things that don't work at the moment do (hopefully) with the new profile.  If that works you can then import one by one the files and folders from the .mozillold back to the new profile, checking each time until you find the probem config file.

Hope that helps.

---

### Post by blikkboks on 2008-08-11
I tried reinstalling but that did not help and i cant find any ./firefox folder.

---

### Post by ajgreeny on 2008-08-11
In nautilus hit Ctrl+H to show hidden files and folders, then look for **.mozilla** folder not **.firefox** in your home.

---

### Post by blikkboks on 2008-08-11
It worked! Thanks!

---

### Post by tphillippe on 2008-10-29
Exact same issue for me.  Disable of plugins didn't work.  Reinstall didn't work.  Some corrupt profile issue.  Renamed and imported back, all is fine.

---

