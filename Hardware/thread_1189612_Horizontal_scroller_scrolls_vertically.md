---
title: "Horizontal scroller scrolls vertically"
date: 2009-06-16
forum: Hardware
---

### Post by kylehase on 2009-06-16
I enabled horizontal scrolling through [FONT="Courier New"]system -> preferences -> mouse -> touchpad [/FONT] but when I use the horizontal scroll area of my touchpad it scrolls vertically in some apps (Firefox) and not at all in others (Thunderbird).

I was going to post my xorg.conf but I can't find it in Jaunty. It's not in /etc/X11/.

According to hardinfo my mouse is:
```
Name 	AlpsPS/2 ALPS GlidePoint
Type	Mouse
Bus	0x11
Vendor	2
Product	0x8
Connected to	isa0060
```

Other system details:
[INDENT]Dell latitude E4200
Jaunty 9.04[/INDENT]

---

### Post by TrineH on 2009-06-17
Try this link:

[https://wiki.ubuntu.com/X/Config/Input](https://wiki.ubuntu.com/X/Config/Input)

and go down to the heading:
Input Configuration with HAL

Perhaps this can help you.

---

### Post by kylehase on 2009-06-17
Thanks. That was quite informative but it seems that the mouse configuration GUI is storing the settings elsewhere.  No files in that directory are modified after making changes through the mouse settings tool.  I'd hate to have conflicting settings in two different locations.

The only file in that location is **preferences.fdi**:
```
<?xml version="1.0" encoding="UTF-8"?> <!-- -*- SGML -*- -->
<!-- 
  Some examples how to use hal fdi files for system preferences 
  You can either uncomment the examples here or put them in a seperate .fdi
  file.
-->
<deviceinfo version="0.2">
<!-- 
  The following shows how to hint gnome-volume-manager and other programs 
  that honor the storage.automount_enabled_hint to not mount non-removable
  media.
-->
  <device>
    <match key="storage.hotpluggable" bool="false">
      <match key="storage.removable" bool="false">
        <merge key="storage.automount_enabled_hint" type="bool">false</merge>
      </match>
    </match>
  </device>
</deviceinfo>

```

---

