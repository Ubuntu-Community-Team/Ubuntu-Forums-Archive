---
title: "The startup theme..."
date: 2008-07-31
forum: General Help
---

### Post by Animeniac on 2008-07-31
I installed the KDE in my Ubuntu computer. Everytime I start the computer with Ubuntu, I get the Kubuntu startup/shutdown theme (NOT in the login screen). Also the theme of the GRUB boot menu has changed into the Kubuntu theme that has a dark highlight bar, and the background color is black.

How can I change the startup/shutdown theme from Kubuntu back to Ubuntu?
And how can I change the theme of the GRUB boot menu?

---

### Post by ajgreeny on 2008-07-31
If you mean the usplash screen, normally the enlarging orange bar with the word ubuntu above, you can get it back by using command ```
sudo update-alternatives --config usplash-artwork.so
``` in terminal and choosing which one you want.  Interestingly whenever I used it it didn't change both the startup and shutdown but just one (can't remember which) so I got the one back that I wanted by uninstalling the other one with synaptic.  Do a search for usplash if you want to do the same to get you ubuntu usplash back.

About the grub part, I can't help as I thought the two systems were the same, just showing a simple menu on black background unless you changed it yourself.  I didn't think there was a grub theme at all in either.  For some possibly useful info look at the txt file attached.

---

### Post by pi.boy.travis on 2008-07-31
You can change upsplash themes with Startup-Manager.  Install it via synaptic.  It will be in System-Administration.  Additional themes can also be installed via synaptic.

---

### Post by Animeniac on 2008-07-31
The Startup manager really helped. Not only can I change the usplash theme, but I can also change the text and background colors. Thanks for your help, guys.

---

### Post by pi.boy.travis on 2008-07-31
It comes in real handy.  BTW if you ever have to edit menu.lst try QGRUBEditor.  Also really easy to use.

---

