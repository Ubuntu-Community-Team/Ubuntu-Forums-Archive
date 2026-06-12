---
title: "How to keep HP-Toolbox from loading at startup?"
date: 2009-03-10
forum: Hardware
---

### Post by Murrquan on 2009-03-10
Hi, all! I've got an HP Deskjet printer/scanner all-in-one, and as soon as I plugged it in Ubuntu helpfully installed the HP Toolbox software for me. Apparently this will make it easier for me to manage it and scan things with it or something.

I don't need it just to print things out, though. And from an aesthetic perspective, I don't like having it there in my system tray, or autoloading an application that appears to use QT on my nice, neat Gnome desktop.

I've just been closing it every time I boot up. How can I keep it from loading altogether, or make it so that it only loads when I need it (or so I can trigger it manually)? And if the only thing I can do is remove it, how do I keep it from auto-installing again once I plug my printer back in?

Any help would be appreciated! Many thanks!

---

### Post by MiguelS. on 2009-03-10
Hello, 

Go to System->Preferences->Sessions, and look for HP System Tray Service (under Startup Programs Tab), unticking it should be enough for it not to automatically start-up again.

Make sure though, you know how to start the program if you need it (I think is also under system->preferences)

Hope that helps,
MiguelS.

---

### Post by Murrquan on 2009-03-10
Ah, okay! Many thanks!

---

