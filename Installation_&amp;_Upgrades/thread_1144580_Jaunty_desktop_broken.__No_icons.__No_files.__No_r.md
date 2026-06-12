---
title: "Jaunty: desktop broken.  No icons.  No files.  No right click."
date: 2009-04-30
forum: Installation &amp; Upgrades
---

### Post by jajodo on 2009-04-30
Clean install from Intrepid.  Home on separate partition.
Since install the desktop does not function.
The panels are fine.
During bootup there is a longer than expected pause with a black wallpaper.
Finally the standard Ubuntu wallpaper appears.
However there are no drive icons, the right click does not work, and files in the desktop folder do not appear on the desktop.  Nautilus otherwise works fine.

Google lists many similar posts over the past several years.  Has anyone found a fix for this?  Thanks in advance.

---

### Post by karanm83 on 2009-05-01
Same thing has been happening to me, but did work initially. 

I have found that if I go to the terminal or Run Application (Alt+F2) and type 'nautilus' it opens the nautilus file explorer and somehow reactivates the desktop. 

I don't know why this works and it has to be done every time I restart but it does seem to work for the current session. I will let you know if I find out anything more, but so far I have not been able to replicate this any other way

---

### Post by jajodo on 2009-05-02
Thanks... you helped me.
I believe nautilus was not loading at all automatically.
This worked for my system:
Go to System>Preferences>Startup Applications
Click "add" application
Under command type nautilus
Logged back in and life is good.

---

