---
title: "Compiz Fusion has stopped working at login (8.04)"
date: 2008-09-18
forum: General Help
---

### Post by clutterskull on 2008-09-18
I have been running Compiz Fusion with Hardy for about a month now. Just starting yesterday Compiz won't start when I log in. All other applications start fine but all I see is the application windows with no borders and they cannot be moved. If I restart compiz (either with fusion-icon or compi --replace) it all comes up normally.

Any suggestions?

---

### Post by amedac on 2008-09-18
Try to add Fusion-icon in startup programs

---

### Post by prshah on 2008-09-18
> **clutterskull said:**
> I have been running Compiz Fusion with Hardy for about a month now. Just starting yesterday Compiz won't start when I log in. 

You can check / add the "compiz --replace" command to your startup sessions by System-Preferences-Sessions. If it's already there, use the "compiz --replace" command, then System-Preferences-Sessions-Session Options-Remember Currently Running Applications.

Logout, restart X server with Ctrl_Alt_BkSpace (optional, but thorough) and log back in; does it work now?

---

### Post by jpeddicord on 2008-09-18
This might seem obvious, but check System > Preferences > Appearance and go to the Visual Effects tab. Set it to None, then back to whatever you had it on previously (Normal/Extra/Custom). Sign out and back in and it might work.

---

