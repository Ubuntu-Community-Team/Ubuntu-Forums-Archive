---
title: "No display after boot ubuntu 10.04 beta"
date: 2010-04-21
forum: Hardware
---

### Post by mvmacd on 2010-04-21
I just got a new laptop, installed ubuntu 10.04 beta, and was trying the effects out. 
I pressed Shift+F9, for the water effect, and it froze my laptop up completey [this worked fine on ubuntu 9.10]. ctrl+alt+backspace didn't work, nor ctrl+alt+del, still just a black screen. So I hold power, and boot it again, it's fine. So then I go enable another effect on compiz [Forgot which one :(], and that finished off my display for good. Now I boot, and breifly see the "default keyring unlock" screen, then it goes black. Nothing works. I even tried "recovery mode" on the boot menu. It too is black. :( 'cept if I press ctrl+alt+del it shows a blue screen on the top, and then proceeds to shut down...
I think compiz is keeping my system to work... is there a way to boot into a shell? then I could do sudo apt-get remove compiz.

Thanks
Matt

---

### Post by nerdy_kid on 2010-04-21
boot from livecd and remove the executible permissions of the compiz binary should fix it.  or just delete the binary all together.  then you can uninstall it smoothly once youve got the system up again.

---

