---
title: "need help editing icons from theme"
date: 2008-09-15
forum: General Help
---

### Post by macvr on 2008-09-15
hi, 
i'm a noob, i trying to edit the icons from a theme[Aero-CrazyFolk-RC1]
i dont know where i got it from... but it has a wonderful set of icons but since it is RC1 its not yet finished... so i edited the icons using GIMP, renamed them to to work correctly and completed most of it ...[took nearly 3days!!!mostly since i was a noob]

BUT i'm stumped with a few problems
    i'm not able to properly name the icon for 
1-create document,
2-create folder, 
3-the DEFAULT favicon[sheet with globe] that is by used by firefox for sites which dont have specific favicons
4-how do i change the icon for recent documents?

5-how do i make hidden folders display with different icon when they are visible?[now all folders are displayed with same icon]

---

### Post by macvr on 2008-09-16
Bump?

---

### Post by robz0rz on 2008-09-16
Those marked with a star are links to the first one (in my icon-theme). Obviously the same icons as .png's exist in the various sized folders.


**1)**
scalable/actions/document-new.svg
scalable/actions/filenew.svg *
scalable/actions/gtk-new.svg *


**2)**
scalable/actions/folder-new.svg


**3)**
scalable/mimetypes/text-html.svg
scalable/mimetypes/gnome-mime-application-xhtml+xml.svg *
scalable/mimetypes/gnome-mime-application-x-php.svg *
scalable/mimetypes/gnome-mime-text-html.svg *
scalable/mimetypes/html.svg *
scalable/mimetypes/www.svg *


**4)**
scalable/actions/document-open-recent.svg


**5)**
I never knew this was possible. What icon-theme did you find that has this? As far as I know, it's not even possible at all, but I hope you can prove me wrong, for this is something I'd like to change myself as well!

---

### Post by macvr on 2008-09-16
1-4] i had labelled the icons with the exact names,
 but all the icons are .png so are all the other icons, NO .svg in this theme[Aero-CrazyFolk-RC1]

but if the labelling is correct why dont only these icons work?

5] it doesnt work but this unfinished theme has the icon for hidden folders, so thought that there might be a way...!

---

### Post by macvr on 2008-09-17
anyone has any ideas how to solve this?

---

### Post by robz0rz on 2008-09-19
Please open the icon-themes index with your favourite editor and copy-paste it in here. Opening it can't be done from Nautilus without some sort of "Open with..." script, so your best bet is to type in the following in terminal:

```
gedit ~/.icons/<icon-theme-name>/index.theme
```


Also, please provide a link to the download of the theme, so i can take a look at it myself.

---

### Post by macvr on 2008-09-19
> **robz0rz said:**
> 
Also, please provide a link to the download of the theme, so i can take a look at it myself.
[http://www.gnome-look.org/content/show.php/Aero-CrazyFolk-RC1?content=67198]("http://www.gnome-look.org/content/show.php/Aero-CrazyFolk-RC1?content=67198")

found it!!!... i initially forgot where i got this set... its been only updated in oct2007!!!

but has a wonderful set of icons, and i GIMPed a few icons myself...:)

[COLOR="Blue"]hei... do u know how to display hidden folders, when made visible ,with a different icon?[/COLOR]

---

### Post by macvr on 2008-09-19
> **robz0rz said:**
> 

```
gedit ~/.icons/<icon-theme-name>/index.theme
```


```
[Icon Theme]
Name=Aero-CrazyFolk-RC1
Comment=Aero-CrazyFolk-RC1 CrazySoilder.RC1
Directories=scalable/apps,scalable/filesystems,scalable/mimetypes,scalable/devices,scalable/emblems,scalable/stock,scalable/status,scalable/places

[scalable/emblems]
Size=128
Context=Emblems
Type=scalable

[scalable/apps]
Size=128
Context=Applications
Type=scalable

[scalable/devices]
Size=128
Context=Devices
Type=scalable

[scalable/filesystems]
Size=128
Context=FileSystems
Type=scalable

[scalable/mimetypes]
Size=128
Context=MimeTypes
Type=scalable

[scalable/stock]
Size=128
Context=Stock
Type=scalable

[scalable/status]
Size=128
Context=Status
Type=scalable

[scalable/places]
Size=128
Context=Places
Type=scalable
```
i'v changed the emblems size to 128 only now[initially it was 256]
> previously i didnt know how to open the icon.theme

PS:when it was 256 and made all the emblems look tiny,so i had to the size the size of all emblems to 256 , now since i was able the access the icon.theme i'v edited it to 128 and the icons to 150...

---

### Post by macvr on 2008-09-20
bump?

---

### Post by macvr on 2008-09-30
bump?

---

### Post by macvr on 2008-10-15
bump?

---

