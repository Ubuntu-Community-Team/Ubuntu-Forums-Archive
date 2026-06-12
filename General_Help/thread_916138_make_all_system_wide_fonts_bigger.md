---
title: "make all system wide fonts bigger"
date: 2008-09-10
forum: General Help
---

### Post by ELD on 2008-09-10
Basically i have a new 22" widescreen monitor at the optimum resolution the manual says the fonts are a little small.

How can increase all wording in the system to a little bit bigger?

---

### Post by unutbu on 2008-09-10
Go to System>Preferences>Appearance. Click on the Fonts tab. Click on the Details button. Increase the Resolution (measured in dots per inch) to make some system fonts appear bigger. 

Note that some applications will ignore this GNOME setting. For these applications you will have to configure the font size manually. Usually this can be done by clicking on Edit>Preference. 

If that doesn't work, name the app and perhaps someone here will know the way.

---

### Post by cariboo on 2008-09-10
You got the information just a little bit wrong, you don't change the resolution to change the font size, Go to System-->Preferences-->Appearance-->Fonts.
See the attached screenshot. Just click the the size button and change the font size. In my case you can see it is set at 12.

Jim

---

### Post by unutbu on 2008-09-10
Oh yes! How silly of me :)
Thanks, cariboo907.

---

### Post by ELD on 2008-09-11
Yeah i have done that, my next problem is the login screen is way way way off, the login box appear nearer the right bottom corner than the centre and cuts the rest off? :S

---

### Post by unutbu on 2008-09-11
Perhaps try
```
sudo apt-get install startupmanager
```

startupmanager can configure your login screen resolution.

---

### Post by unutbu on 2008-09-11
Sorry, I think I might have been wrong about this.
Instead, perhaps try this:
[http://ubuntuforums.org/showpost.php?p=4997526&postcount=8](http://ubuntuforums.org/showpost.php?p=4997526&postcount=8)

---

