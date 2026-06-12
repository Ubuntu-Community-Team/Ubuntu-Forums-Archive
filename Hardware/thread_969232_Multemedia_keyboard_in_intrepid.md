---
title: "Multemedia keyboard in intrepid"
date: 2008-11-03
forum: Hardware
---

### Post by eddarl on 2008-11-03
I upated to intrepid Friday.
I now find my keyboard has very strange keyboard behavior.

When working in a terminal. up arrow gives me a screen capture screen, right arrow restarts X. 

I have a Microsoft wireless 3000 multimedia keyboard.

Keyboard Preferences show it as a Microsoft Multimedia Keyboard 1.0A

When I look at keyboard shortcuts I do not see any settings that would cause this. However, none of the multimedia keys seem to work. The arrow keys also do not function properly.

---

### Post by the mage on 2008-11-17
> **eddarl said:**
> I upated to intrepid Friday.
I now find my keyboard has very strange keyboard behavior.

When working in a terminal. up arrow gives me a screen capture screen, right arrow restarts X. 

I have a Microsoft wireless 3000 multimedia keyboard.

Keyboard Preferences show it as a Microsoft Multimedia Keyboard 1.0A

When I look at keyboard shortcuts I do not see any settings that would cause this. However, none of the multimedia keys seem to work. The arrow keys also do not function properly.
I confirm this. 
I have the same problem, same keyboard, after upgrading to intrepid (or with a clean install) the multimedia keys don't work.
I have seen this reported on launchpad I think, and it must be a kernel issue if I am not wrong...
Any solutions ?

---

### Post by ///MVinny on 2008-12-07
Same here - noticed it after changing the hostname and the up key opens the screencap dialog box.

---

### Post by ///MVinny on 2008-12-07
I found something on another post, added to /etc/X11/xorg.conf

```
Section "ServerFlags"
     Option "AutoAddDevices" "False"
EndSection
```

Strange but it fixed the issue.

---

### Post by Hooya on 2009-01-19
This worked for me as well.  Thank you.  It also solved some global shortcut issues in Amarok for me.

---

