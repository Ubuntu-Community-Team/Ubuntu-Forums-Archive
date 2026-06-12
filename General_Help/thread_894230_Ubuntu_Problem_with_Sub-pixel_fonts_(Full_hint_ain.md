---
title: "Ubuntu Problem with Sub-pixel fonts (Full hint ain't working correct)"
date: 2008-08-19
forum: General Help
---

### Post by NeverWinter. on 2008-08-19
Here's a pic with Full hunting as can be easily seen,check the fonts and how sharp they are:

[[IMG]http://www.imageshack.gr/files/5u7mwlutj4s75soloqct.png[/IMG]](http://www.imageshack.gr/view.php?file=5u7mwlutj4s75soloqct.png)

Then,there's a picture of how it is with Slight Hunting and as you can see it's way better:

[[IMG]http://www.imageshack.gr/files/t5wd8u3u7qc9hvf3ixjk.png[/IMG]](http://www.imageshack.gr/view.php?file=t5wd8u3u7qc9hvf3ixjk.png)

Yesterday everything was fine before i installed 2 Packages of a game called "Assault Cube" then the hinting became like this...sry for the big size but i have Twin Monitors.

Hope somebody could help me fix this issue :)

I Also tried:
```
sudo dpkg-reconfigure fontconfig-config
sudo dpkg-reconfigure fontconfig
```

But nothing changed! =/

---

### Post by NeverWinter. on 2008-08-19
I Think i've found something:

That's in my xorg.conf:

```
Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
```

Thought there's no X11 folder or X11/rgb inside my /usr/X11R6/lib/

---

