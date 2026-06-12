---
title: "desktop info in writing how do i do that..."
date: 2008-10-10
forum: General Help
---

### Post by Vertoxic on 2008-10-10
Hi all, so how do i get all the writing on the desktop that displays all sorts of stuff/pc info etc..

Like this guy for example?

[http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-19.jpg](http://i480.photobucket.com/albums/rr169/Arch-newb/Screenshot-19.jpg)

---

### Post by Denestria on 2008-10-10
```
sudo apt-get install conky
```

[There are some config files posted here.](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)

---

### Post by Vertoxic on 2008-10-11
> **Denestria said:**
> ```
sudo apt-get install conky
```

[There are some config files posted here.](http://ubuntuforums.org/showthread.php?t=281865&highlight=conky)
thank you, ok so i did that and were is the menu for all this ?

---

### Post by OutOfReach on 2008-10-11
Follow the link that Denestria posted, it has configuration files. Save those configuration files in your home directory as .conkycrc
Then launch conky like this:
```
conky -c ~/.conkyrc
```

or if you want conky's default configuration just go into a terminal and execute:
```
conky
```

---

### Post by Denestria on 2008-10-11
Conky doesn't have a menu item.  Once you have a .conkyrc configuration file saved to your /home/username you can start it by typing **conky** into the run dialog (alt-f2) or **conky&** in a terminal.

---

### Post by Vertoxic on 2008-10-11
thanks guys :) 1 more thing how do i make it completely transparent? cause its just like a window on my screen

---

### Post by Denestria on 2008-10-11
My config is:

own_window yes
own_window_transparent yes

I'm not sure if it is the same for Gnome especially if you are using Nautilus to draw the desktop.

---

