---
title: "Is there any way to get transparent window borders"
date: 2008-09-17
forum: General Help
---

### Post by iampriteshdesai on 2008-09-17
I want transparent windows border as in Vista. Is there any theme to give Ubuntu an Vista like look?

---

### Post by fracturedmorals on 2008-09-17
```
sudo apt-get install emerald
``` 

Then alt+f2:
```
emerald --replace
```

For preferences and the ability to install themes:
System > Preferences > Emerald Theme Manager

For themes:
[www.gnome-look.org](www.gnome-look.org)

---

### Post by iampriteshdesai on 2008-09-17
I installed Emerald and tried the code, but I couldn't notice any change!

---

### Post by howefield on 2008-09-17
don't think there are any themes bundled with the emerald install, you need to go and find 'em first, then import into emerald and you can use emerald --replace

here is another link as well to add to the one above [http://www.compiz-themes.org/index.php?xcontentmode=103](http://www.compiz-themes.org/index.php?xcontentmode=103)

---

### Post by fourthofjuly on 2008-09-17
check out [http://gnome-look.org]("http://gnome-look.org") and see the section on gtk-2 themes... lots of them...

---

### Post by iampriteshdesai on 2008-09-17
Actually I use Ubuntu Ultimate, so I have Emerald with lots of themes preinstalled.
I checked it. So why isn't the new theme still activated?

---

### Post by howefield on 2008-09-17
have you tried running the command after selecting you choice of theme ?

emerald --replace

---

### Post by iampriteshdesai on 2008-09-17
I tried it still hasn't cahnged!

---

### Post by Calmatory on 2008-09-17
Same here. No change, even after I imported a few themes. :|

---

### Post by mike1234 on 2008-09-17
Make sure you have desktop visual effects enabled under "appearance". If you have compiz fusion launched sometimes you have to select windows manager on right click.

M.

---

### Post by Calmatory on 2008-09-17
> **mike1234 said:**
> Make sure you have desktop visual effects enabled under "appearance". If you have compiz fusion launched sometimes you have to select windows manager on right click.

M.

Thank you. Solved the problem. :)

---

