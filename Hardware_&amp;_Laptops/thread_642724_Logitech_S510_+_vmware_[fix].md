---
title: "Logitech S510 + vmware [fix]"
date: 2007-12-16
forum: Hardware &amp; Laptops
---

### Post by seamuso on 2007-12-16
Just got a Logitech S510 and set it up using all the info from all of the posts +  some minor key remapping so that amarok used most of the keys I wanted to use (thanks for all of the info) .. I launched vmware last night and started hardy for an update and noticed that my keys no longer worked correctly ..

up arrow = screenshot, no delete, etc

edit /usr/lib/vmware/config and add the following at the end -
```

xkeymap.nokeycodeMap = true

```Here's the link to all of the vmware keycode info .. [http://www.vmware.com/support/gsx25/doc/devices_kbmap_gsx.html](http://www.vmware.com/support/gsx25/doc/devices_kbmap_gsx.html)

---

