---
title: "Window frames just dissapeared."
date: 2008-08-18
forum: General Help
---

### Post by Uner on 2008-08-18
Well, I was setting up my 2nd display, I restarted, and the windows didnt seem to have window frames anymore(You know... the thing you hold-click and drag to move the window)...
What I did before that occured is...

sudo apt-get install nvidia-settings
gksudo nvidia-settings
and then messed around, and changed some settings when trying to get it working. Then restarted, and it automatically went to Safe graphics mode. I restarted, and logged in.

Halp.

edit - When I open a terminal window, just a white square comes up. I can still type in, but all I see is a blank box.

---

### Post by Elfy on 2008-08-18
Do Alt+F2 and paste this command in

```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```logout and login and they should be back.

---

### Post by smo0th on 2009-02-16
try this:

```
gtk-window-decorator --replace &
```

it worked for me :)

---

### Post by johenkel on 2010-04-06
> **smo0th said:**
> try this:

```
gtk-window-decorator --replace &
```

it worked for me :)


That worked for me too.
Hopefully still after a reboot !!! 

*fingertwist*

---

