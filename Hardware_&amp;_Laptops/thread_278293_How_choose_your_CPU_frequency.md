---
title: "How choose your CPU frequency"
date: 2006-10-16
forum: Hardware &amp; Laptops
---

### Post by JimmyJoe on 2006-10-16
After reading through some post on this and other ubuntu forums I have found a solution how to manage your cpu speed and power mode on your own and don`t let the machine choose it for you. Here:

[http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling](http://ubuntu.wordpress.com/2005/11/04/enabling-cpu-frequency-scaling)

you can find some usefull info.

All you have to do is to run 

sudo dpkg-reconfigure gnome-applets

 and answer "yes" to the following question. After that add CPU frequency Scaling Monitor to panel then richt click on it and select to show in menu frequencies and governors. Now by left clicking on the monitor you can choose the frequency and governor as well. :mrgreen:

---

### Post by atonello on 2006-10-27
Thank you for the useful tip!

---

### Post by ShadowVlican on 2006-10-27
now to somehow remember this when i install ubuntu on my laptop...

---

### Post by toddward on 2006-11-04
Definitely exactly what I was looking for.

---

### Post by grumman on 2006-11-05
ty, exactly what i needed :)

---

### Post by manzuk on 2006-11-11
Super, this is what I was looking for, thank you SO much!
Just one more question, it might be out of topic: I've got a Dell laptop, and it seems to me that when working under Ubuntu it's hotter than when under Win. Does CPU frequency have something to do with this? I've already installed some utils to control laptop fans, but I don't really know how should them be configured...
OK, thank you again!!!

---

### Post by frogotronic on 2006-11-11
> **manzuk said:**
> Super, this is what I was looking for, thank you SO much!
Just one more question, it might be out of topic: I've got a Dell laptop, and it seems to me that when working under Ubuntu it's hotter than when under Win. Does CPU frequency have something to do with this? I've already installed some utils to control laptop fans, but I don't really know how should them be configured...
OK, thank you again!!!

Use i8k (install it from Synaptic)

Check this POST:

[http://www.ubuntuforums.org/showthread.php?t=31147&highlight=i8k](http://www.ubuntuforums.org/showthread.php?t=31147&highlight=i8k)

---

