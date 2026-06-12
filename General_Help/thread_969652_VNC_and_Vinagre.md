---
title: "VNC and Vinagre"
date: 2008-11-03
forum: General Help
---

### Post by glenmo on 2008-11-03
okay...

i am running Hardy.  i have GDM over VNC working just great; when i vnc to my machine it asks me to login and i do so and all is great.

however, i would like to add extra functionality.  i would like to be able to either

a) get the gdm login screen if i go to myMachine:0

or

b) get my current x session on vinagre if i go to myMachine:1

is this even possible, or would i have to divide by zero to do it?

---

### Post by glenmo on 2008-11-04
i got it!

configuration editor > desktop > gnome > remote access give it a non-standard port, enable it.

i also went to /etc/services and added vinagre 5902/tcp #vinagre to the end of file


woohoo!

---

