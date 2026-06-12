---
title: "Logitech MX1000 button assignment question"
date: 2008-11-15
forum: Hardware
---

### Post by GmAz on 2008-11-15
Ok, I have my buttons as I want them except for two.  I want the side scrolling buttons (when you move the wheel left and right) to switch between my desktops.  in my .xbindkeysrc file, I commented out:

#"echo ButtonRelease 13 ButtonPress 6 ButtonRelease 6 | xmacroplay -d 0 :0.0"
#  b:13
#"echo ButtonRelease 14 ButtonPress 7 ButtonRelease 7 | xmacroplay -d 0 :0.0"
#  b:14

and added:

"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Alt_L]\[Left]""
  b:13
"/usr/bin/xvkbd -xsendevent -text "\[Control_L]\[Alt_L]\[Right]""
  b:14

Button 13 and 14 are the side scroll buttons, but the assignments aren't recognizing.  I know you can use the normal up and down scroll to switch desktops, but only if you can click the desktop then scroll.  I want to just use the side scrolls for that.  I never use those buttons to side scroll anyways so they are essentially wasted.  

In 8.10, the side scrolling seems to work without any modification to anything, so where can I disable 8.10 from defaulting them to side scrollnig so xbindkeys can take over and use it for changing my active desktop?

---

