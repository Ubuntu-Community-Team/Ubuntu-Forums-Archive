---
title: "Simdock problems"
date: 2008-08-26
forum: General Help
---

### Post by dmiller40 on 2008-08-26
I have had simdock installed twice now one on ubuntu hardy and now on xubuntu. The dock works really well but there is a small block around it for when the icon enlarge that is suppose to be "transparent" where my wallpaper is suppose to be. But instead it is a small block of the hardy heron "weird bird looking thing" wallpaper. I can post a screen if need be.

thanks
dm

---

### Post by starcannon on 2008-09-10
same problem here, am going to try wbar and see if it does any better.

---

### Post by fermin on 2008-09-30
I think your SimDock is not recognizing your background image for some reason. You can try setting the background image manually by running SimDock from terminal (or with Alt+F2) with:
```
simdock -y -b /path/to/your/wallpaper
```

The -y option is for it being above all other windows and -b is for setting the background manually. If your want to run this at start up, add it to your session options. I hope this helps.

---

### Post by Sader on 2009-03-19
Just wanted to check with Simdock users - any Idea how to make simdock stay above maximized windows with changing backroud in accordance with window maximized...?
Presently it just displays the same background image set up in properties...

---

### Post by aeon.flux on 2010-01-06
hello there, i have a different problem :( the i fist started simdock, it seemed to work ok, but i tryed to set some things it was ok. then it asked to restart do apply changes, so restarted the simdosk. when i started it again, no changes that i wanted to do had been done.  there was only a firefox icon, that looked like a question mark and error windows opened to note that a firefox icon was not found. but i didn't wanted and firefox there :( i wanted 10 other stuff...

so the sindock looks like not working on 9.04?

---

