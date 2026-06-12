---
title: "Direct rendering with ati mobility 9000"
date: 2007-11-04
forum: Hardware &amp; Laptops
---

### Post by Panos on 2007-11-04
Hello all,

I have installed Gutsy in my Travelmate 800LCI laptop and everything works fine. Compiz is working great, with all sorts of effects. However, I would appreciate some information about the message I get when checking "glxinfo | grep rendering". The response is "Direct rendering: no (LIBGL_ALWAYS_INDIRECT set)".

As far as I can understand, that means my graphics card runs without hardware acceleration. On the other hand, glxgears gives some pretty good fps, around 1000 or more. I googled a lot but I can't figure out if indirect rendering is caused by compiz or some missing settings in xorg.conf. The installed driver is the ati open-source one. 

In any case, how much do I miss by not having direct rendering, and how can I enable it?

Many thanks in advance

Panos

---

### Post by sparX CG on 2007-11-04
Not having direct rending is definitely a problem on this card. I know because I have one. :P

I do have a solution too, I just figured it out today. It's pretty simple, actually, just install the libgl1-mesa-dri package, or something like that. You'll find it in Synaptic.

Good luck! :)

EDIT: Right, I posted the solution here too. -> [http://ubuntuforums.org/showthread.php?t=587039&page=2](http://ubuntuforums.org/showthread.php?t=587039&page=2)

---

### Post by Panos on 2007-11-05
Thanks a lot. I'll try it as soon as I go home and I'll post the results.

---

