---
title: "change theme from terminal"
date: 2008-09-07
forum: General Help
---

### Post by JayeD on 2008-09-07
My first baby is due at the end of the month and this will cause the family to start flooding over to my house. I'm sorting out a script that will remove the girly picture setup I have and change it for a more suitable view.
I've sorted out the screensaver pictures, but now want to sort out the theme. I have some themes set up in gnome-appearance-properties, but I don't know how to switch between them in script. Anyone else know?

---

### Post by Diabolis on 2008-09-07
Execute: ```
gconf-editor
```

Its like a windows registry, but is used by gnome to manage the preferences of the user. What you want to use in your script are "gnome keys".

An example of how to use them:
[http://ubuntuforums.org/showthread.php?t=898798&highlight=gconftool-2](http://ubuntuforums.org/showthread.php?t=898798&highlight=gconftool-2)

That link is about changing the wallpaper. For the themes you'll find the keys here: **/ desktop / gnome / interface**

---

### Post by JayeD on 2008-09-07
hmm, thanks but it's not quite what I had in mind. I've already got themes set up in the gnome-appearance-properties and really just want to load them up. The index files are stored .themes, I just want to load them.

---

### Post by JayeD on 2008-09-07
Ok, I downloaded the source code of the theme gui and it uses imports the theme files to itself and then sets gconf values, so I've taken what you said and made my script load the keys that I have copied out from the same files. Works a treat. Thanks.

---

