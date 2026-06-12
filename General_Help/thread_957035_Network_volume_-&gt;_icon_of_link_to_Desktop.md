---
title: "Network volume -&gt; icon of link to Desktop"
date: 2008-10-23
forum: General Help
---

### Post by garydauphin on 2008-10-23
I would like to figure out how to do one think that I do on both Mac and Windows:  put a link (shortcut) to network volumes on the Desktop, so that to mount them, all I have to do is double click.

I cannot figure out how to do this in Ubuntu.  Any help out there?

Where are the mounts for network volumes in the file system?

---

### Post by powerbookluv111 on 2008-11-06
I'm sorry no one has answered your question by now. You can do a few different things. If you want an icon on the desktop to "Network" also found under "Places" in the panel. You can type:
 
gconf-editor 

in terminal and a little application will open. Next, expand the arrow next to "Apps" and then expand "Nautilus" select "Desktop." You can then check the boxes next to the items that you want to appear on your desktop such as the "Computer" icon, the "Trash" icon, or the "Network" icon. 

Secondly, if you simply want an icon on the desktop to open a single location, you can right-click on the desktop and select: "Create Launcher" under "type" select "Location" and then you'll have to enter the location of the network share. The order of this location is usually:

smb://[workgroup]/[ip address or hostname]/[share]

That's assuming it's an SMB share mount. 

Hope that helped.

---

### Post by cogitordi on 2008-12-24
Thanks -- you showed me how to switch off this behaviour. (o:

---

