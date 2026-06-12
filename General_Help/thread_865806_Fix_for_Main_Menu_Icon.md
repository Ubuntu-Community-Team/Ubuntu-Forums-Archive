---
title: "Fix for Main Menu Icon"
date: 2008-07-21
forum: General Help
---

### Post by j42 on 2008-07-21
Hi, my default main menu icon and in the 'add to panel' got altered recently to orb. This happened when I tried to tweak my desktop to look like Vista using the Aero Clone theme. Basically I use screenlets to install the orb but failed. Refer to the image below:

[[IMG]http://img156.imageshack.us/img156/3234/bendbu6.th.jpg[/IMG]](http://img156.imageshack.us/my.php?image=bendbu6.jpg)

Aero-Clone theme link: [http://www.filesend.net/download.php?f=2f04a0a52f62c32cf567343cece836b4](http://www.filesend.net/download.php?f=2f04a0a52f62c32cf567343cece836b4)

I've already clean uninstalled screenlets, what's left now is to fix the icons to the default. Help me please!

btw, I'm new to Linux O:)

---

### Post by Tim Sharitt on 2008-07-21
I've looked at the script in the theme which changes the icon so the following should change it back
```
sudo cp start-here.png start-here.png.old
sudo cp start-here.png.old2 start-here.png
```
then to see if it works hit Alt-F2 and enter
```
killall gnome-panel
```

---

### Post by j42 on 2008-07-21
I entered the first command but then it says, "cp: cannot stat `start-here.png': No such file or directory" :|

---

### Post by Tim Sharitt on 2008-07-21
Sorry, the first command is
 ```
cd /usr/share/icons/gnome/32x32/places/
```
I got a little ahead of myself there.

---

### Post by j42 on 2008-07-21
I tried but it didn't work. But have a look at the screenshots below please, I realized all of my default 32 pixels icons have been changed to orb.

[[IMG]http://img155.imageshack.us/img155/1404/shot1vi4.th.jpg[/IMG]](http://img155.imageshack.us/my.php?image=shot1vi4.jpg)

[[IMG]http://img339.imageshack.us/img339/6471/shot2ch6.th.jpg[/IMG]](http://img339.imageshack.us/my.php?image=shot2ch6.jpg)

And I don't have backup files either. If you could upload your default 32 pixels Ubuntu Icons then it would be great so that I can replace them manually :-D

---

### Post by Tim Sharitt on 2008-07-21
Here is the one from my machine [http://tsharitt.net78.net/start-here.png]("http://tsharitt.net78.net/start-here.png")

---

### Post by j42 on 2008-07-21
Thank you, it has been fixed! :mrgreen: :mrgreen: :mrgreen:

---

