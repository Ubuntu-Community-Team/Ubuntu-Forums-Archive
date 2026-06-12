---
title: "Font Rendering Issue"
date: 2008-11-24
forum: General Help
---

### Post by kg87 on 2008-11-24
I've ran into a strange problem which I didnt have in Hardy, 

Basically, i like the M$ font "Calibri", and tried to set it to run throughout metacity, However it doesnt seem to be rendering properly there. instead im presented with Rectangles. (see image attached). 

Is there anyway to resolve this???

(the font displays correctly when used in open office)

---

### Post by blazemore on 2008-11-24
There are known issues with this font.

Do you have Office 2007 installed on Windows? If you do, copy the relevant .ttf files into /home/yourname/.fonts (you might have to create this directory), or /usr/share/fonts.

Delete any instances of the font from /usr/share/fonts first
```
sudo rm -rfv /usr/share/fonts/*calibri*
```

---

### Post by kg87 on 2008-11-24
ok there's a bit of an update

in /usr/share/fonts/font-install

there are a series of M$ fonts that i'd copied previously, and all of them have the font icon with an "x" in the top right of it. so i presume that means they aren't working.

---

### Post by blazemore on 2008-11-24
Yeah delete them, and install the fonts you want manually, from an Office 2007 installation, (look in C:\Windows\Fonts)

I *think* you can install the Office 2007 trial in Wine, and then copy them over from /home/foo/.wine/drive_c/Windows/Fonts or similar.

Copy them to /usr/share/fonts
```
sudo cp -rfv /path/to/old/calibri* /usr/share/fonts
```

---

