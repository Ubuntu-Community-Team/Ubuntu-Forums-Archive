---
title: "Custom Icon Installation"
date: 2008-11-09
forum: General Help
---

### Post by OneRingShort on 2008-11-09
I'm trying to install a custom icon theme I made, but whenever I install it, it only loads a few of the icon and references to a different icon set for the rest.

I went to gnome-look.org and downloaded the "Footwork" icon set, and decided I wanted a custom look.  Since I don't know a lot about making these things, I figured I'd do it the "easy" way and just replace the icons, while keeping the names and index.theme intact.

After I got everything finished, I archived it, and installed it.  Some of the icons load, such as those in the drop down menus on the panels, but all of the folders and file icons still reference the original theme.  I have no idea what is going on here, and was hoping someone with a bit more knowledge on the subject would be able to help.

If I can get it working, I'll upload it so you guys can try it out.

Thanks in advance,

Matt

[Edit] Here is the index.theme file in case it may be part of the problem.  I checked all the directories listed, and all of the icons were in their proper place.
```
[Icon Theme]
Name=Vekter Blue
Comment=A modification of the "Red Icons" theme and the "Footwork" theme. All scalable icons are from the "Footwork" theme because I'm too lazy and hate working with vector graphics.


Directories=16x16/actions,16x16/apps,16x16/categories,16x16/mimetypes,16x16/places,16x16/status,22x22/actions,22x22/mimetypes,22x22/places,22x22/status,24x24/actions,24x24/apps,24x24/categories,24x24/devices,24x24/emblems,24x24/mimetypes,24x24/places,24x24/status,32x32/apps,32x32/devices,32x32/emblems,48x48/apps,48x48/categories,48x48/devices,48x48/emblems,48x48/mimetypes,48x48/places,48x48/status,48x48/stock/generic,128x128/apps,128x128/devices,128x128/mimetypes,128x128/places,128x128/status,scalable/apps,scalable/devices

[16x16/actions]
Size=16
Context=Actions
Type=Fixed

[16x16/apps]
Size=16
Context=Applications
Type=Fixed

[16x16/categories]
Size=16
Context=Categories
Type=Fixed

[16x16/mimetypes]
Size=16
Context=Mimetypes
Type=Fixed

[16x16/places]
Size=16
Context=Mimetypes
Type=Fixed

[16x16/status]
Size=16
Context=Status
Type=Fixed




[22x22/actions]
Size=22
Context=Actions
Type=Fixed

[22x22/categories]
Size=22
Context=Categories
Type=Fixed

[22x22/mimetypes]
Size=22
Context=MimeTypes
Type=Fixed

[22x22/places]
Size=22
Context=Places
Type=Fixed

[22x22/status]
Size=22
Context=Status
Type=Fixed



[24x24/actions]
Size=24
Context=Actions
Type=Fixed

[24x24/apps]
Size=24
Context=Applications
Type=Fixed

[24x24/categories]
Size=24
Context=Categories
Type=Fixed

[24x24/devices]
Size=24
Context=Devices
Type=Fixed

[24x24/emblems]
Size=24
Context=Emblems
Type=Fixed

[24x24/mimetypes]
Size=24
Context=MimeTypes
Type=Fixed

[24x24/places]
Size=24
Context=Places
Type=Fixed

[24x24/status]
Size=24
Context=Status
Type=Fixed




[32x32/apps]
Size=32
Context=Applications
Type=Fixed

[32x32/devices]
Size=32
Context=Devices
Type=Fixed

[32x32/emblems]
Size=32
Context=Emblems
Type=Fixed




[48x48/apps]
Size=48
Context=Applications
Type=Fixed

[48x48/categories]
Size=48
Context=Categories
Type=Fixed

[48x48/devices]
Size=48
Context=Devices
Type=Fixed

[48x48/emblems]
Size=48
Context=Emblems
Type=Fixed

[48x48/mimetypes]
Size=48
Context=MimeTypes
Type=Fixed

[48x48/places]
Size=48
Context=Places
Type=Fixed

[48x48/status]
Size=48
Context=status
Type=Fixed

[48x48/stock/generic]
Size=48
Context=Stock
Type=Fixed




[128x128/apps]
Size=128
#MinSize=32
#MaxSize=128
Context=Applications
Type=Fixed

[128x128/devices]
Size=128
#MinSize=32
#MaxSize=256
Context=Devices
Type=Fixed

[128x128/mimetypes]
Size=128
#MinSize=32
#MaxSize=256
Context=MimeTypes
Type=Fixed

[128x128/places]
Size=128
#MinSize=32
#MaxSize=256
Context=Places
Type=Fixed

[128x128/status]
Size=128
#MinSize=32
#MaxSize=256
Context=Status
Type=Fixed



[scalable/apps]
Size=128
MinSize=48
MaxSize=256
Context=Applications
Type=Scalable

[scalable/devices]
Size=128
MinSize=48
MaxSize=256
Context=Devices
Type=Scalable
```

---

