---
title: "How do I un install this?"
date: 2008-07-25
forum: General Help
---

### Post by jras20 on 2008-07-25
I downloaded a Casino game but it doesn't do what I thought.  How can I un install it?  I downloaded Rushmore Casino. I could'nt get it to run.  
On another note does anyone know of a good slot machine game for Ubuntu?
Thanks.

---

### Post by caljohnsmith on 2008-07-25
> **jras20 said:**
> I downloaded a Casino game but it doesn't do what I thought.  How can I un install it?  I downloaded Rushmore Casino. I could'nt get it to run.  
On another note does anyone know of a good slot machine game for Ubuntu?
Thanks.
How did you install it? Did you compile it yourself with ./configure, make, sudo make install or similar? Or was it a .deb file?

---

### Post by jras20 on 2008-07-25
It was a setup.exe file from wine.
Not a big deal I'd just like to get rid of it when I can.

---

### Post by caljohnsmith on 2008-07-25
If it's installed under Wine, just go to your Wine menu and select "Uninstall Wine Software". That application will give a list of your installed Windows programs, and you can uninstall from there.

---

### Post by geirha on 2008-07-25
If you installed it to the default location, you'll find it if you browse to the hidden folder ".wine" in your homefolder (hit Ctrl+H to toggle showing hidden files and folders), then "drive_c" and further to the folder it's installed in. See if there is any uninstall.exe among the installed files, and see if that works. If not, just delete the folder in Program Files.

If this is the only program you have installed with wine, the easiest thing is to just remove the .wine folder all together. A new, clean one will be created next time you run wine.

---

### Post by jras20 on 2008-07-27
Thanks I got it deleted.

---

