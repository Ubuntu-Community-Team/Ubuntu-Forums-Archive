---
title: "how to make wicd use nm-applets icons?"
date: 2008-08-23
forum: General Help
---

### Post by markp1989 on 2008-08-23
i recently installed wicd, to replace nm-applet, i dont like the icons really, is there any way i can make wicd use the nm-applet icons? 

thanks markp1989

---

### Post by 67GTA on 2008-12-26
I'll give this a bump. I'm doing the same. Haven't figured out where the icons for wicd are kept yet. Maybe someone will help give us a clue:)

---

### Post by 67GTA on 2008-12-26
I just figured it out. When I was looking at this before, I had several other things in my brain, and wicd icons fell out:) Look at the package properties in synaptic to see where every file a package touches when installed. The networkmanager (nm-applet) icons are in /usr/share/icons/hicolor/22x22/apps. The wicd icons are in /usr/share/pixmaps/wicd. If you completely removed(purged) networkmanager, the icons for it will be gone. You could just reinstall/uninstall to get them back, and then remove the residual packages. Check to see if you still have them. Then you will have to open nautilus as root and rename the icons. Rename the low signal strength icon for nm-applet to whatever the wicd equivelant is, and move it to the wicd folder and so on.

---

### Post by 67GTA on 2008-12-26
More good news! I just found what we were looking for. There is a link in this thread for nm-applet icons for wicd signal strengths. [http://ubuntuforums.org/showthread.php?t=566965](http://ubuntuforums.org/showthread.php?t=566965)

---

