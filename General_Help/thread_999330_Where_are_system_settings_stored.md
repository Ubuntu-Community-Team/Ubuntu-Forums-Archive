---
title: "Where are system settings stored?"
date: 2008-12-01
forum: General Help
---

### Post by Hartbuntu on 2008-12-01
I need to change system settings but because my graphic interface is currently not working, i need to be able to change system settings from the terminal. I am running ubuntu intrepid 8.10. Are the system settings stored in a file that i would be able to edit from the terminal? Or is there an easier way to change system settings through the terminal? 

Thanks,
Hartbuntu

---

### Post by stoneage on 2008-12-01
If it is a graphics display problem, you are probably looking for /etc/X11/xorg.conf

> gksudo gedit /etc/X11/xorg.conf

If you just want to change the resolution, can you access System => Preferences => Screen Resolution?

---

### Post by Hartbuntu on 2008-12-01
actually, i need to change my system settings so that it auto logs in as my user. On the login screen, i keep getting a "Authentication failed" error and it wont go away so i want to change it back to auto login and then ill find the answer from there. I currently do not hae access to my computer, im using vista on my brothers.

---

