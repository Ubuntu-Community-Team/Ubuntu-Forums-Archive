---
title: "Usb stopped working, Modprobe eating all my resources"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by Acglaphotis on 2007-04-11
Hi

I just got this stuff out of the blue sky, i turned on my laptop (after hibernating vista), i selected my kernel, and everything is fine, until the loading screen suddenly stops on "Loading hardware drivers", so i wait, and then wait some more...it too 5 minutes altogether just to say that "Loading hardware drivers" failed, when normally my system takes 30s to start up. Then i log on, and noticed things are running very slowly, i think, "Ahw, it must be this 386 kernel i picked instead of the 686smp ( i got dual-core)", so i restart select 686 and the "Loading hardware drivers" failed again. i wonder what isnt working and then log on, and then i discovered that my usb mouse wasnt working, and that everything was running slow. so i open up my system monitor a notice that some process is eating 100% of my resources on one CPU. I went to see what process it was and i didnt find anything. Then i opened the terminal wanting to see the result of "top" and found out that my beloved cpu was being eated by Modprobe, then i typed "C" to see the output (/sbin/modprobe -Q usb:v0572pCB01d0100dcFFdsc00dp00ic00isc00ip00) i didnt really knew what to do with the output so i posted it here.

All i did was update some stuff yesterday from the little orange and white icon on the top bar, the one left to the clock. It said that i had some stuff to update so i did. Could that be the reason behind this?

Any ideas?

Should i reinstall ubuntu? (I was thinking of upgrading to Feisty Fawn)

Acgla

PS: Im running Dapper, on a pavilion dv2000. turion 64x2, dual booting vista and ubuntu.

---

