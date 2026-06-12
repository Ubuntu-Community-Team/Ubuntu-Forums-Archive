---
title: "Howto Create .deb for Fonts?"
date: 2009-08-14
forum: Installation &amp; Upgrades
---

### Post by Chillawowa on 2009-08-14
There is a vast plethora of classy fonts, however their installation is time consuming. Therefore I was thinking of packaging a set, such as hand-drawn, grunge, and/or professional fonts into a .deb package. I have already arranged several groups of fonts, the only missing part is the packaging.

I have searched for howto's to compile .deb, but there seems to be no documentation for fonts.

It is apparent that they have to be placed into the ~/.fonts directory, but are there additional config files?

I have a rudementary knowledge on compilation, and adequate experience on the cmd line, such as '|' and common commands.

Mit freundlichen Grüßen,
Moritz

---

### Post by ad_267 on 2009-08-14
If you are creating a .deb package they would go in /usr/share/fonts so they are available for all users.

You could look at the structure of an existing package I guess, here's what the ttf-liberation package looks like:
```
/.
/etc
/etc/defoma
/etc/defoma/hints
/etc/defoma/hints/ttf-liberation.hints
/usr
/usr/share
/usr/share/doc
/usr/share/doc/ttf-liberation
/usr/share/doc/ttf-liberation/README
/usr/share/doc/ttf-liberation/AUTHORS
/usr/share/doc/ttf-liberation/copyright
/usr/share/doc/ttf-liberation/changelog.Debian.gz
/usr/share/fonts
/usr/share/fonts/truetype
/usr/share/fonts/truetype/ttf-liberation
/usr/share/fonts/truetype/ttf-liberation/LiberationMono-Bold.ttf
/usr/share/fonts/truetype/ttf-liberation/LiberationMono-BoldItalic.ttf
/usr/share/fonts/truetype/ttf-liberation/LiberationMono-Italic.ttf
/usr/share/fonts/truetype/ttf-liberation/LiberationMono-Regular.ttf
/usr/share/fonts/truetype/ttf-liberation/LiberationSans-Bold.ttf
/usr/share/fonts/truetype/ttf-liberation/LiberationSans-BoldItalic.ttf
/usr/share/fonts/truetype/ttf-liberation/LiberationSans-Italic.ttf
/usr/share/fonts/truetype/ttf-liberation/LiberationSans-Regular.ttf
/usr/share/fonts/truetype/ttf-liberation/LiberationSerif-Bold.ttf
/usr/share/fonts/truetype/ttf-liberation/LiberationSerif-BoldItalic.ttf
/usr/share/fonts/truetype/ttf-liberation/LiberationSerif-Italic.ttf
/usr/share/fonts/truetype/ttf-liberation/LiberationSerif-Regular.ttf
```

Edit: This might help, [http://wiki.debian.org/Fonts/PackagingPolicy](http://wiki.debian.org/Fonts/PackagingPolicy)

---

