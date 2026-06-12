---
title: "Upgraded memory"
date: 2006-03-16
forum: Hardware &amp; Laptops
---

### Post by DarkAngel88 on 2006-03-16
Hi, 

I recently upgraded my memory on my laptop.  I had 512 mb of ram and I succesfully installed 1gb of ram.  My system detects the 1 gb of ram but under linux, when I open the system monitor, under ressources, I see the 1 gb of ram available but the system never use more than +/- 400 mb of ram.  Is there a way to tell ubuntu to use more than 400 mb of ram for example ?  Mabye I have to tell him to use the whole memory...  Even with vmware running, I get about 300 mb of used memory with 1 gb of cache memory...

Thanks

Sorry for my bad english... :S

---

### Post by blackant on 2006-03-16
Interesting, I just upgraded mine to 1gb too. :P
But I don't really notice any changes...except as it detected as 1gb memory...

---

### Post by Swab on 2006-03-16
Are you using the 686 kernel?  I think there might be a lower memory limit with the 386 kernel.

---

### Post by DarkAngel88 on 2006-03-16
Actually I'm using the 386 kernel.  Is there a way to raise the memory limit on the 386 kernel ?

---

### Post by DarkAngel88 on 2006-03-20
Anyone please ?

---

### Post by bluevoodoo1 on 2006-03-20
I know that when you compile your own kernel there is an option for "high memory support." But by default it is enabled, and only makes a difference if you have more than 4 GB ram. Since the options are "off," "up to 4 gb" and "over 4 gb."

You're probably not doing any tasks that involve your system to use more than the 400 MB or so that it's been using. I have 1 gig ram and it rarely goes over 400 as well. But to make a point, here's a screenshot of stats showing the following programs open/running...

gnomebaker
xmms
cd-ripper
cd-player
k3b
konqueror
nautilus
Eterm
conky
xine
Bittornado x3
firefox
gimp (with a 490 mb image)
gaim
audacity
mplayer
open office writer
gedit

a few others (can't remember)...

note it says there are 130 processes, normally there are between 75-85 and the ram is at 621 of 1004 mb. With only 12mb of 2 gb swap used. After closing all the apps., there are currently 83 processes and the RAM is back down to 316 MB.

I've used the 386 and 686 kernels and it's the same. I bet if you were to keep pushing your system, you'd see the RAM usage increase. So after all that... it seems your system is normal.

---

### Post by DarkAngel88 on 2006-03-20
Thanks, glad to see that I'm "normal" ;)

I'll try to load my system to see some differences !!

---

