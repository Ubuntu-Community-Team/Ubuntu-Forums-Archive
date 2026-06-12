---
title: "Affter logined and no desktop showed"
date: 2007-07-14
forum: Hardware &amp; Laptops
---

### Post by cnshzj007 on 2007-07-14
I can login successfully.
But then no desktop showed.
any help?

---

### Post by SendDerek on 2007-07-14
What do you mean by "Desktop"?  Is it the desktop wallpaper, or is it the whole gnome/kde interface?  Do you have any panels?  What happens when you hit Alt+F2?  Does it bring up the "Run Application" dialoge?



Edit:  I now see that you're a Gutsy Gibbon testing user.  Now, I'm thinking that you probably know what you're doing and the problem is more serious than I expected.  I'm not sure if I'm going to be able to help.

---

### Post by cnshzj007 on 2007-07-14
**It is not a desktop wallpaper, it is [COLOR="DarkOrange"]a whole color[/COLOR]screen. No any panels.**

---

### Post by w4ett on 2007-07-14
You are using Gutsy?...I'm not surprised...it's in Alpha testing......

Maybe a xserver bug?...can you get to a command prompt? sounds like you need to review your debug logs and see where we are.

---

### Post by cnshzj007 on 2007-07-14
[COLOR="DarkOrange"]**This is the screan color.**[/COLOR]

---

### Post by cnshzj007 on 2007-07-14
Yes, I can login with super terminal.

---

### Post by w4ett on 2007-07-14
What happens when u log into Gnome failsafe mode?

---

### Post by w4ett on 2007-07-15
I checked the Gutsy Dev Forum....Here is the thread that u need regarding your orange screen/no desktop crash:   

[http://ubuntuforums.org/showthread.php?t=501086](http://ubuntuforums.org/showthread.php?t=501086)

Good luck with the testing!

---

### Post by cnshzj007 on 2007-07-15
Gnome safe mode is the same result as the gnome mode.

---

### Post by cnshzj007 on 2007-07-15
follow these steps to solve the problem :
sudo apt-get install icewm
then choose icewm to log in and log out
enter into gnome terminal to do the order"sudo apt-get autoremove --purge icewm"
then choose gnome to log in.
then sudo gnome-apperance-propertity shutdown the desktop effect.

---

