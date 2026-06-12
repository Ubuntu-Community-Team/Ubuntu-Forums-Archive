---
title: "HOWTO: Get your mouse's side button's to work in Firefox"
date: 2006-08-31
forum: Hardware &amp; Laptops
---

### Post by dannyalberici on 2006-08-31
If you work with Windows and a mouse that had side buttons such as the Microsoft Intellimouse Optical, then you're probably used to using the side buttons as back and forward buttons in your browser.  By default, Linux is not configured to do this but you can do it by modifying your /etc/X11/xorg.conf as follows:

```
sudo nano -w /etc/X11/xorg.conf
```

Under the section 
```

"InputDevice"
        Identifier      "Configured Mouse"
```

add the lines 

```
Option "Buttons" "7"
Option "ButtonMapping" "1 2 3 6 7"


```

save the file (ctrl+o) and exit (ctrl+x).
restart your browser and enjoy!

---

