---
title: "zd8000 external monitor switching problem"
date: 2008-06-21
forum: Hardware
---

### Post by awambawamb on 2008-06-21
hi all.

i've just installed linux ubuntu on my "old" HP pavilion zd8000. seems that everything works except for the "special" buttons on my laptop. this includes MONITOR SWITCHING.

now, the problem is that i always use that laptop at home, and i have a bigger 22" screen to use. to save power and lifespan of my laptop, i used to switch ONLY on the external monitor. now this seems to be impossible to do, since when i press "fn"+"F4" on my laptop, both screens became black for a few seconds but nothing really changes. they keep to show both the same things.

I want to be able to switch from my latop monitor to the external one, is it possible? and how?

---

### Post by awambawamb on 2008-06-21
it is nice to see that nobody want to share their knowledge to me. thanks.

this is the problem of linux. everyone thinks that some "problems" are so basic that everyone should be able to write lines and lines of code to solve the problem...

sorry for disturbing everyone here...

---

### Post by Matsuri on 2009-02-15
I've got the same problem. Upon pressing the "fn" key and hitting the external monitor button, both screens become active. If you have an nVidia graphics card, you can enter the nVidia control panel through the System->Administrator->NVidia X Server Confi and through that control panel deactivate your laptop screen, and activate only the external. You can then set the proper screen resolution to your monitor then apply the changes. You can also save these settings to your xorg.conf file for future reference.

One time only thing. I'm still searching for a perm. solution. But this will get you by until we you can figure out how to get it to be automatic upon pressing the "fn" key.

Matsuri

---

