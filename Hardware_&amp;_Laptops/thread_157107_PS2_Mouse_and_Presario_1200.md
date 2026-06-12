---
title: "PS/2 Mouse and Presario 1200"
date: 2006-04-08
forum: Hardware &amp; Laptops
---

### Post by Micke.Breath on 2006-04-08
Thought I'd try and save some other poor soul the hours of frustration I went through trying to get my external PS/2 mouse to work on my Presario 1200 laptop.  I tried everything (turning off the Synaptics touchpad, playing with xorg.conf) - nothing worked until I discovered psmouse.  So to get the external mouse to work I did

open terminal

sudo gedit /ext/modules

find the line that has plain ole psmouse and change to

psmouse proto=imps

save and reboot

You should have your mouse (both of them in fact) on your next login.

---

### Post by Micke.Breath on 2006-06-04
I found that after I upgraded to Dapper (6.06) my ps/2 mouse that had been working using the workaround above stopped working again - but thanks to others I found the solution.

open a terminal

sudo gedit /etc/rc.local

then type in

modprobe -r psmouse
modprobe psmouse proto=imps

I placed this before the exit 0 line

save and restart - should have your ps/2 mouse back - again

---

