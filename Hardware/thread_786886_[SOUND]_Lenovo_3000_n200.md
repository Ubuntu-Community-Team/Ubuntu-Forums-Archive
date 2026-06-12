---
title: "[SOUND] Lenovo 3000 n200"
date: 2008-05-08
forum: Hardware
---

### Post by nastyguard on 2008-05-08
Greetings, oh the great ubuntu forums comunity! Well straight to the point. We bought a laptop for my mom today and it came with Ubuntu 7.10 (I upgraded to 8.04 shortly after that)

OK the problem is, that I installed ubuntu like I always do. And there are problems with the sound. There was no sound when we installed 7.10, and the same was when we upgraded to 8.04 via update manager. I hope people reply soon because my mom will be home soon and we want the little surprise to work out fine and with the sound so please reply ASAP. :)

Best regards, Nasty.

---

### Post by nastyguard on 2008-05-08
bump
BUMP
BUMP!!!

Please help!!!

---

### Post by fogey on 2008-05-25
hi Nasty, I didn't have sound either but now I do (with ubuntu 8.04 like your mom).  One of the forums recommended pasting the code from [http://www.w1ldt4ng3nt.net/blog/item/77](http://www.w1ldt4ng3nt.net/blog/item/77) .  This did the trick for me.  good luck

---

### Post by Technobabel on 2008-06-25
Hi,

you may want to try the following out:
open a terminal 
sudo su
edit /etc/modprobe.d/alsa-base
add at the end of file:
options snd-hda-intel model=lenovo
save & exit
done! 
Oh you should turn the mic of otherwise it'll kill your ears :)
It worked for me.

Best,
Tech

---

### Post by tauseen123 on 2008-06-26
I did that work around too.. or a similar one found in the forums. The problem is; My sound is working fine but when I plug in the Headphones the speakers won't go out! I tried the switching thing in the Volume Controller but to no avail. 

Help! :D


Here is what I added to 
/etc/modprobe.d/alsa-base

options snd-hda-intel single_cmd=1 model=lenovo


Does that single_cmd=1 thing makes a difference ? :S

---

### Post by tauseen123 on 2008-06-26
Got it sorted.. My bad! Sorry! :D


Just 'muted' the FRONT. :D (hehehe)


Thankyou! \\:D/

---

