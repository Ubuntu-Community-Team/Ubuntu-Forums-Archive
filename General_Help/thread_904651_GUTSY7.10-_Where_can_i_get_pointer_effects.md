---
title: "GUTSY7.10- Where can i get pointer effects?"
date: 2008-08-29
forum: General Help
---

### Post by KEE on 2008-08-29
it would be real cool if i could find the best place where to get animations for my current mouse pointer. thanks in advance =D

---

### Post by Shazaam on 2008-08-29
One place....
[http://www.gnome-look.org](http://www.gnome-look.org)

---

### Post by KEE on 2008-08-29
> **Shazaam said:**
> One place....
[http://www.gnome-look.org](http://www.gnome-look.org)

How would someone install mouse and icon themes? Its a .tar.gz so i suspect its a drop to somwhere but i dont know where to put it. i tried in /usr/share/icons but i cant make a file there or drop that folder there either. i get "command error" =/ how do i install these type of themes?

---

### Post by Shazaam on 2008-08-29
System>Preferences>Appearance.

---

### Post by KEE on 2008-08-29
> **Shazaam said:**
> System>Preferences>Appearance.
 hmm no luck. i can do this to icon themes but not mouse themes =/ is there a way to install mouse themes?

---

### Post by geezerone on 2008-08-30
To install a mouse theme you will need to copy an uncompressed folder theme to /usr/share/icons directory but as this is owned by root do this as 'sudo'.

A nice mouse theme can be found *[COLOR=Blue][here.]("http://gnome-look.org/content/show.php/Grounation+%28developers+version%29?content=66050")[/COLOR]*

Download to Desktop, uncompress then open a terminal and cd to Desktop. Then type:

```
sudo  cp -r *<folder name on desktop>* /usr/share/icons

```Then go to System > Preferences > Appearance. Click on Customise at bottom of window and then the rhs tab which is 'pointers' Then select your new theme (in the above hyperlinked theme it would be 'Grounation').

Hope this works for you.

---

### Post by KEE on 2008-08-31
> **geezerone said:**
> To install a mouse theme you will need to copy an uncompressed folder theme to /usr/share/icons directory but as this is owned by root do this as 'sudo'.

A nice mouse theme can be found *[COLOR=Blue][here.]("http://gnome-look.org/content/show.php/Grounation+%28developers+version%29?content=66050")[/COLOR]*

Download to Desktop, uncompress then open a terminal and cd to Desktop. Then type:

```
sudo -r *<folder name on desktop>* /usr/share/icons

```Then go to System > Preferences > Appearance. Click on Customise at bottom of window and then the rhs tab which is 'pointers' Then select your new theme (in the above hyperlinked theme it would be 'Grounation').

Hope this works for you.

thanks it work but i get a mix of default and the new theme. should i delete the default pointers? how do I since it wont allow me to place in the trash XD

---

