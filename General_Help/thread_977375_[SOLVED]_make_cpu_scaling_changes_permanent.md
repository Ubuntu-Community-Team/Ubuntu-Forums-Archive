---
title: "[SOLVED] make cpu scaling changes permanent"
date: 2008-11-10
forum: General Help
---

### Post by bryncoles on 2008-11-10
title says it all here. i added the cpu scaling applet to my task bar and changed it from 'on demand' to 'conservative'. im happy with the results. but after a reboot, its back to 'on demand', and i have to change it back to my preferred option of 'conservative' again. 

is there a way to make the changes permanent, so after i reboot the cpu scaling is still 'conservative'?

im running intrepid on a dell inspiron 1525n, if that helps.

cheers!

---

### Post by sdennie on 2008-11-10
I don't advise setting the governor to conservative but, you should be able to make it permanent if you add the following to /etc/rc.local:

```

cpufreq-selector -g conservative

```

That may not work across a suspend/resume though.  Though not specifically for your laptop, this guide is for a similar(-ish) laptop and you may find some useful information about power savings (which, it sounds like you are trying to do if you are changing the CPU governor): [ HOWTO: XPS m1330 power savings]("http://ubuntuforums.org/showthread.php?t=847773")

---

### Post by bryncoles on 2008-11-10
cheers! ill look into that, and possibly try and read up on why conservative might not be such a good idea... then maybe do it anyway ha ha ha!

---

### Post by sdennie on 2008-11-10
> **bryncoles said:**
> cheers! ill look into that, and possibly try and read up on why conservative might not be such a good idea... then maybe do it anyway ha ha ha!

Haha.  It won't cause your machine to explode either way so, I'll be happy to help you do it even if I don't recommend it.  ;)

---

### Post by bryncoles on 2008-11-10
ive made the change to /etc/rc.local. ill post back tomorrow when ive had chance to find out if it works over suspend and resume, and rebooting. now, might i ask, why is it not recommended....?

---

### Post by sdennie on 2008-11-10
> **bryncoles said:**
> ive made the change to /etc/rc.local. ill post back tomorrow when ive had chance to find out if it works over suspend and resume, and rebooting. now, might i ask, why is it not recommended....?

Power savings sometimes isn't intuitive.  There are two variables at play.  One is the CPU frequency and the other is the CPU idle (or sleep) state.  Your computer probably spends most of its time idle and modern chips recognize this fact and switch into a very low power state when nothing is happening (they do this often and fast).  With that in mind, the *faster* you make your chip run, the quicker it can return to a deep sleep state and, as such, save power.  The idea is called "Race to idle".

---

### Post by bryncoles on 2008-11-10
i see... interesting! though ive noticed having been running on conservative since about 9am that my cpu temp is 2 degrees lower than normal, which strikes me as being a good thing! that said, its only 42 degrees, so its not like it was abnormally high anyway...

---

