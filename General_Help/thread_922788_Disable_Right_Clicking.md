---
title: "Disable Right Clicking"
date: 2008-09-17
forum: General Help
---

### Post by rybl on 2008-09-17
Does anyone know of a way to disable right clicking?  Ideally I would like a right click to just act as a left click, but completely disabling it would also be an acceptable solution.

---

### Post by Taxman415a on 2008-09-17
I don't, but what for? It sounds like you want to do it for another reason, so it may be better to just ask the best way to do what you are trying to do. Then maybe somebody here will have some experience with that.

If you want to lock down what the user can change, try the lockdown editor in the administration menu (under the System menu). I can't remember if it is installed by default, but if it is not, the package is called pessulus, so try ```
sudo aptitude install pessulus
``` to install it if not.

---

### Post by rybl on 2008-09-18
I am using pessulus right now to lock down some settings in Epiphany. The specific problem I am running into right now is that even after locking things in epiphany down the user is still able to right click on the menu bar and uncheck the show menu bar option.  Then there is no way to get it back without unlocking things because I have disabled menus.  Disabling right clicking seemed like the best option because there are other things, like right clicking on the desktop, that I do not want users to do.  Getting the epiphany thing fixed is my first priority however.

---

### Post by Taxman415a on 2008-09-18
Ahh, yeah sorry, don't know. But googling turned up some links that might help, the best of which was [http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/ch-ddg-lockdown.html](http://www.redhat.com/docs/manuals/enterprise/RHEL-4-Manual/desktop-guide/ch-ddg-lockdown.html)
[http://live.gnome.org/Pessulus](http://live.gnome.org/Pessulus) also mentions asking for help at #pessulus channel on irc.gnome.org so that wouldn't be a bad place to start. I don't know if pessulus can do that, but they would be good people to ask.

---

