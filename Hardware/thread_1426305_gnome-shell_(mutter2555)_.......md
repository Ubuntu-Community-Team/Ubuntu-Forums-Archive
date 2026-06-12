---
title: "gnome-shell (mutter:2555): ......"
date: 2010-03-10
forum: Hardware
---

### Post by luca219 on 2010-03-10
hi, 
I have a problem with the use of gnome-shell on my laptop. 
I have a HP6710 with video card Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller.
I use ubuntu 9.10, practically when start the gnome-shell in command line I have many errors  
"(mutter: 2555): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id <Id_pool-> array-> len 'failed "
and the view is very slow and unstable.
I assume that is a problem with the video card, because I have onother installation in different hardware ,almost the same configuration, but other video card works at 
perfection. 
would anyone have any suggestions? 

thanks

---

### Post by fanum on 2010-03-11
> **luca219 said:**
> hi, 
I have a problem with the use of gnome-shell on my laptop. 
I have a HP6710 with video card Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller.
I use ubuntu 9.10, practically when start the gnome-shell in command line I have many errors  
"(mutter: 2555): Clutter-CRITICAL **: clutter_id_pool_lookup: assertion `id <Id_pool-> array-> len 'failed "
and the view is very slow and unstable.
I assume that is a problem with the video card, because I have onother installation in different hardware ,almost the same configuration, but other video card works at 
perfection. 
would anyone have any suggestions? 

thanks

I was having different video related errors on my 855gm Intel chipset. My solution was to upgrade to the Xorg Edgers PPA (got it from ubuntu tweak), but this caused my machine to freeze regularly. I eventually disabled the Edgers repo, and installed the "Tester" repo. I had to force downgrade my xserver-intel (using synaptic)to stop it from freezing, but the dependencies stayed at the edgers level. I would trying the "Testing" repo, but would not go above it. Also are you using the gnome-shell from the Ubuntu repos? Or ricotz PPA?

---

