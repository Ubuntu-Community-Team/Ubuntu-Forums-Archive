---
title: "Desktop is empty and nothing from places drop down menu will load..."
date: 2009-02-19
forum: Installation &amp; Upgrades
---

### Post by thermobee on 2009-02-19
I uninsalled the bluetooth app( and all the apps that had anything to do with it) thinking i wont need it on my desktop. As soon as i did that my whole desktop disappeared and even my trash icon on the bottom right corner is gone.

I realized what i did so i went back and installed it again, but nothing. I tried switching file managers to Thunar and that did do it either. 

Now when i do click on Thunar File Manager I can find all my files including the stuff that i had on my desktop, but i have no idea how to bring everything back to normal.

Please help me out ,any ideas are appreciated.
Thank you in advance

---

### Post by thermobee on 2009-02-19
bump

---

### Post by thermobee on 2009-02-19
If i try to click on folders such as music, documents and pictures i get this message

No application is registered as handling this file

---

### Post by Crusher on 2009-02-19
Which version of ubuntu are you using?
Which bluetooth package did you remove? (its name)

---

### Post by thermobee on 2009-02-19
ubuntu 8.10
bluetooth analyzer (i reinstalled it tho), it also made me uninstall all the programs related to the analyzer

---

### Post by thermobee on 2009-02-19
Interesting thing is that the computer icon is showing from the Places drop down menu and it works but if drag it onto the desktop it just disappears.

---

### Post by Crusher on 2009-02-19
It sounds like you might have uninstalled the Ubuntu file manager.

Open up a terminal and try
```
sudo apt-get install ubuntu-desktop
```

You might have to logout and then log back in for it to work.

Let me know how it goes.

---

### Post by thermobee on 2009-02-19
anyone?

---

### Post by thermobee on 2009-02-19
> **Crusher said:**
> It sounds like you might have uninstalled the Ubuntu file manager.

Open up a terminal and try
```
sudo apt-get install ubuntu-desktop
```

You might have to logout and then log back in for it to work.

Let me know how it goes.
doing it now

---

### Post by thermobee on 2009-02-19
yup it worked, thank you for your help

---

### Post by Crusher on 2009-02-19
No worries

---

### Post by running_rabbit07 on 2009-07-15
> **Crusher said:**
> It sounds like you might have uninstalled the Ubuntu file manager.

Open up a terminal and try
```
sudo apt-get install ubuntu-desktop
```You might have to logout and then log back in for it to work.

Let me know how it goes.

Just wanted to throw out there that I just had the same problem and this fixed it. I uninstalled the Bluetooth program from Synaptic and lost my file manager.

"Thank You" Crusher and the forum managers that didn't delete this thread.

---

### Post by crstrand on 2009-08-13
I'm using 9.04 Jaunty Jackalope.
I uninstalled Bluetooth also thinking it was rediculous to load it when my desktop will never have bluetooth.
Anyway, I got the dreaded, "no application is registered as handling this file" when trying to use the 'file manager'.
I reinstlled the bluetooth stuff and gnome-panel (I read that in some other thread) to no avail.
Reinstalling ubuntu-desktop did the trick!
 
Thanks be to Ubuntu forums!
 
Is there any way to uninstall an app without clobbering everything it depends on (which other apps may also depend on)?

---

