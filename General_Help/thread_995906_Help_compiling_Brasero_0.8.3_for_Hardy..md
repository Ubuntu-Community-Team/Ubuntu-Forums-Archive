---
title: "Help compiling Brasero 0.8.3 for Hardy."
date: 2008-11-28
forum: General Help
---

### Post by exploder on 2008-11-28
I am trying to compile Brasero 0.8.3 for Hardy to try and solve some problems. I have never compiled a package before and have tried to follow the included documentation with no luck.

Can someone that has compiled this package walk me through this?

---

### Post by taurus on 2008-11-28
When you said no luck, what was the error message?

---

### Post by exploder on 2008-11-28
When I run ./configure I get this.

No package 'gstreamer-0.10' found
No package 'gstreamer-plugins-base-0.10' found

I have these packages installed, I checked. I am trying to follow the install instructions that came with Brasero.

---

### Post by taurus on 2008-11-28
You probably need the -dev (develop) package also when you try to compile something from source.

---

### Post by exploder on 2008-11-28
> You probably need the -dev (develop) package also when you try to compile something from source. 

For gstreamer?

Edit: I installed the -dev packages, now I get this.

No package 'gconf-2.0' found

Is this the proper package name? I can't seem to find it.

---

### Post by exploder on 2008-11-28
Seems to be a never ending problem... I found the last dependency, now this.

No package 'hal' found
No package 'gdk-2.0' found
No package 'gtk+-2.0' found
No package 'dbus-glib-1' found

Edit: I installed all of the gnome-dev packages and it is building now.

---

### Post by exploder on 2008-11-28
Success! My last question is how can I share this package? Where does it store what was built? The new version is installed on my system.

---

### Post by exploder on 2008-11-28
Well, so far this version is still a POS. I tried blanking a DVD-RW and it never did finish the job...I will test burning an iso to DVD next. All of my issues with Brasero have been with DVDs, Cds have not been a problem.

---

