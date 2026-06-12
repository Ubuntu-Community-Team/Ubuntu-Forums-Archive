---
title: "Font Viewer"
date: 2008-11-25
forum: General Help
---

### Post by jdorenbush on 2008-11-25
When viewing my font directories the files no longer have thumbnail previews of the font, it is just a lower case 'a' with a blue arrow running vertical on the left and another one running horizontal on the bottom of the 'a'.

When I try and open I get this error message,

```
Could not display "*font dir here*/*font name here*.ttf".

There is no application installed for this file type
```

So I tried to search around for a font viewer. I've come back empty handed and I rest another one of my many ubuntu problems on the shoulders of the *ubuntu forums community*. :)

---

### Post by boxrec on 2008-11-29
Bump - I have the same problem

---

### Post by BattlePanic on 2008-11-29
I have also noticed this is missing in 8.10.  There seems to be no way to view a preview of a particular font.  Anyone know what program handled this in previous Ubuntu releases?

---

### Post by durand on 2008-11-29
The old font viewer was gnome-font-viewer and it's been deprecated in Gnome 2.23 (The desktop environment) for some strange reason... The two alternatives for GTK are fonty python and fontmatrix but they are both font database viewers rather than single font viewers so there is no good alternative at the moment.

Two relevant bug reports:
[https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/264463](https://bugs.launchpad.net/ubuntu/+source/meta-gnome2/+bug/264463)
[https://bugs.launchpad.net/bugs/216875](https://bugs.launchpad.net/bugs/216875)

Forum post:
[http://ubuntuforums.org/showthread.php?t=908368](http://ubuntuforums.org/showthread.php?t=908368)

---

### Post by durand on 2008-11-30
Edit: Double post

---

### Post by anjanesh on 2008-11-30
Why on earth would they deprecate such a useful feature ?

---

### Post by jdorenbush on 2008-12-02
I guess they didn't go very far in the Bug Report,

> There's no gnome-font-viewer in GNOME 2.23 that was deprecated, closing this report. Also a Bug Tracking System is not the right place to discuss such things you can mail the ubuntu desktop mailing list for example to discuss changing the defaults, thanks in advance.

---

