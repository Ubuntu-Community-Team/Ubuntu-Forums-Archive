---
title: "Ubuntu as a Print Server"
date: 2005-11-29
forum: General Help
---

### Post by mykrob on 2005-11-29
I am a VERY new user to Ubuntu, but have been using Linux for about 2 years now, primarily Suse. Anyway, i have a friend who is looking for something that can run on cheap hardware (P133 with 128MB Ram) to use as a network printer server for an older Xerox copier/printe, oneof the big ones. I am fairly sure that Ubuntu 5.10 would run on it just fine in console mode. My real question is, can Ubuntu be configured to run as a network print server, and if so, can someone help by pointing me to the correct documentation?

Thanks,

-myk

---

### Post by mykrob on 2005-11-30
bump...

---

### Post by soulestream on 2005-11-30
as long as the printer is supported by cups, I would use IPP. It is supported by all versions of linux and windows XP natively. Being as you are using it as a print server samba would be a waste of time.

[http://www.gentoo.org/doc/en/printing-howto.xml](http://www.gentoo.org/doc/en/printing-howto.xml)


gentoo docs are great


soule

---

### Post by skirkpatrick on 2005-11-30
Samba isn't necessarily a waste of time.  I've found that Win98 machines printjobs are faster over Samba and WinXP jobs are faster over IPP, so my machine is setup for both.

---

### Post by soulestream on 2005-12-01
i always forget about those who use 98 :D 


soule

---

### Post by Bandit on 2005-12-01
Myk,
Just thought I would say hi :)
Cheers,
Joey

---

### Post by skirkpatrick on 2005-12-01
Well, my wife loves to play Dungeon Keeper (1 & 2) and it won't run properly under XP and not at all under Wine.

To stay on topic, somebody here had posted this link a while back for a print server on a low-powered machine: [http://www.pigtail.net/LRP/printsrv/](http://www.pigtail.net/LRP/printsrv/)

---

