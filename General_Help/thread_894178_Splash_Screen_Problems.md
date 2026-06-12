---
title: "Splash Screen Problems"
date: 2008-08-19
forum: General Help
---

### Post by jashstud on 2008-08-19
I am a new user to Ubuntu (and Linux in general) but I am enjoying the freedom to customize the interface to my liking. 

I have tried adding a Splash Screen to appear after logging in and before the desktop is booted but have run into some difficulty. It is not that i have been unable to add or activate a splash screen image. (I have done so both manually using gconf-editor and automatically using gnome-splashscreen-manager.) Instead my image appears however it is not centered on the screen such that a large portion of the image is cut off by the lower right hand corner and the upper left hand corner shows the background. 

The resolution of my screen is 1600x1200. Both my 1600x1200 and 1600x1000 images were cut off by that bottom right hand corner. When I tried using an 600x328 image the picture was not cut off but it was clearly not centered and was displayed in the lower right hand area of the screen. 

Has anyone else experienced this issue and is there a method to fix it?
As it is now i have opted to disable my splash screen until I can resolve this issue be cause it really does not look very good. I would greatly appreciate any and all advice and help that can be given. 

Thanks

---

### Post by toemos on 2008-08-20
try changing the virtual resolution under the screen section of /etc/X11/xorg.conf to the resolution you use.

i had this problem a while back, cant quite remember how i fixed it, but i seem to remember that had something to do with it.

---

