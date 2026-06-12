---
title: "HP Pavillion dv1000 series wifi + Multimedia reader"
date: 2005-04-03
forum: Hardware &amp; Laptops
---

### Post by Gandalf on 2005-04-03
hello,
i have HP pavillion laptop, i have wifi card (Intel PRO/Wireless 2200 BG), for the wifi card i followed one of the topics posted here (don't remeber which one exaclty, but i remember that i couldnt modeprobe ipw2200

as for the mulimedia reader (SD-MS/Pro-MMC-SM-XD) i didn't understand how to do it i tried fdisk -l /dev/sd* no devices partion has been found
so how can i use it???

---

### Post by twinmaker on 2005-09-09
[QUOTE=Gandalf]hello,
i have HP pavillion laptop, i have wifi card (Intel PRO/Wireless 2200 BG)...[/QUOTE]
I got the same problem - cannot use the wifi adapter in my HP Pavilion dv1067ea notebook. 
And this is the only reason that stops me from starting using Ubuntu fully.
Thank you

---

### Post by vtec on 2005-09-09
I just got a compaq v2000. Its the silver version of the dv1000 with a few less features. I have the same wireless set up and it worked right out of the box for me, though i havn't tried BT yet. That probley won't help you much but at least you know it should and can work. As for the memory card reader, I have been unable to get that to work. My in based on a TI chip yours should be the same. I don't think there are any drivers for it yet but i'm not positive about that.

---

### Post by Gandalf on 2005-09-09
[QUOTE=twinmaker]I got the same problem - cannot use the wifi adapter in my HP Pavilion dv1067ea notebook. 
And this is the only reason that stops me from starting using Ubuntu fully.
Thank you[/QUOTE]
Man i know how to use it it's easy, just install ipw200 deivers version 1.0.6 ( [http://ipw2200.sourceforge.net](http://ipw2200.sourceforge.net) ) (don't forget to install ieee80211 drivers before the ipw2200, do not forget the firmware after u install the ipw2200 and of course do not forget to remove-old for both ieee80211 and ipw2200 before installing them)

if you need help or you think it's gonna be complicated then tell me i'll try to guide step by step

---

### Post by kewaposoi on 2005-09-13
[QUOTE=Gandalf]Man i know how to use it it's easy, just install ipw200 deivers version 1.0.6 ( [http://ipw2200.sourceforge.net](http://ipw2200.sourceforge.net) ) (don't forget to install ieee80211 drivers before the ipw2200, do not forget the firmware after u install the ipw2200 and of course do not forget to remove-old for both ieee80211 and ipw2200 before installing them)

if you need help or you think it's gonna be complicated then tell me i'll try to guide step by step[/QUOTE]

hi I've read your post, i'm having the same problem, could you help me step by step.  :roll: I'm new in ubuntu. thenks in advance

---

### Post by pdpmalcolm on 2005-09-28
im a total newb. could use step by step too

---

### Post by pek on 2005-12-20
hello!

i would really appreciate if you could point me to a how-to or a step by step guide. tryed google but had no luck :(

---

### Post by Gandalf on 2005-12-20
Here's a HOWTO [http://wael.nasreddine.com/Articles/Articles/howto%3Aipw2200.html](http://wael.nasreddine.com/Articles/Articles/howto%3Aipw2200.html)

---

