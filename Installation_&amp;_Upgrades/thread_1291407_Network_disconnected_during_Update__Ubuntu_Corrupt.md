---
title: "Network disconnected during Update : Ubuntu Corrupt/Crash"
date: 2009-10-14
forum: Installation &amp; Upgrades
---

### Post by madmax.santana on 2009-10-14
I was downloading updates from the internet when my network suddenly got disconnected. After that I restarted my system and found that nothing was working. 
Sound = Gone.
apt-get upgrade = Not Working
Any Application Started = System Crashed

And it was a lot of havoc with my system! I re-formatted it and re-installed it... Luckily I did not have any important data stored so no loss was faced...

I just want to ask tow questions.
    -    Why did it happen? And how to avoid this?
    -    After anything like that happens, is there any way I can restore my Ubuntu system without any data loss to the exact same configuration?

---

### Post by raymondh on 2009-10-14
Hi Madmax.Santana,

Couple of tips:

-  I use [PING ]("http://ping.windowsdream.com/")to clone  my HD (or partition).  That way if it crashes, I have a clone as back-up.
- Separate your /home from root (/).  That allows you to re-install over root (/) alone whilst keeping your /home intact (which, BTW, contains your config files, settings, etc.)

Sorry for the "havoc".  I have experienced such once and it ain't fun.

Regards,

---

### Post by madmax.santana on 2009-10-15
Hay Raymond! Thanks buddy! Thanks a lot... It's really nice someone helping me out...
You see I am absolutely new to Linux and I have been facing too much problems with Jaunty and my laptop (HP HDX)... I have posted quite a lot in the forum and have rarely been helped out... It's really great on your part... 
I'll take care next time and make sure to remember your tips... Thanks a lot...

---

### Post by raymondh on 2009-10-15
You're welcome and happy ubuntu-ing :)

---

