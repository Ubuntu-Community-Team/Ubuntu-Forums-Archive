---
title: "ubuntu 8.04"
date: 2008-09-06
forum: Hardware
---

### Post by denadi21 on 2008-09-06
hi guys im new into ubuntu but i really whant to learn how to use it
I have just installed ubuntu 8.04 into toshiba m45-s265.
it works good but some hardware dont work like sound or usb .
can anyone help me fix this problems

---

### Post by jbrown96 on 2008-09-06
try alsamixer ```
alsamixer
``` use the arror keys and "m" to adjust the channels and see if you can get it working that way.
If that doesn't work, you could try installing the backports in synaptic (linux-modules-backports-hardy-gneric I believe). 
If that still doesn't work, post back with your hardware ```
lspci
``` kernel ```
uname -a
``` alsa version (you can find it at the top of alsamixer).

---

### Post by Sef on 2008-09-06
For future reference, it's best to post one problem in a thread because if two or more problems are posted in a thread, one problem can dominate a thread to the exclusion of the others.

---

### Post by jbrown96 on 2008-09-07
I just reread your problem, and I found some problems exactly like that in the alphas and betas of hardy. Try to enable irqpolling. google it with your model number and you can find some guides.

---

