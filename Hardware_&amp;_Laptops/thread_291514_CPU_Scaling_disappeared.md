---
title: "CPU Scaling disappeared"
date: 2006-11-02
forum: Hardware &amp; Laptops
---

### Post by Falcon.Geek on 2006-11-02
I was working on getting my panel to show a voltage monitor when i rebooted and suddenly no long was able to scale my CPU.  I use my laptop on battery often... i really need to scale it.

Attached is a screenshot of the error it gives me.

And yes it did work about 5 minutes ago.

Thank You :confused:

---

### Post by chriscando on 2006-11-02
Have you changed anything recently, this happend to me when I reinstalled nvidia drivers. My fix might not be what you want to hear but after reinstalling ubuntu it was fixed.

---

### Post by Falcon.Geek on 2006-11-02
is there a way i can "reinstall" ubuntu without reformating and haveing to reinstall all my packages?

I just got everything running well.  I really don't want to lose it all.

---

### Post by chriscando on 2006-11-02
Not sure if you can keep all the packages (would kinda defeat the purpose of a reinstall). But I think you can generate a list of installed packages so you can quickly reinstall them.

Also if you keep your /home partition (dont reformat it) it will keep all of your preferences and settings for programs so after you reinstall them they are back to the way you used them. For example, if I keep my /home partition intact while reinstalling ubuntu, I just have to start firefox and my default profile is automatically used keeping all my bookmarks and settings.

---

### Post by Falcon.Geek on 2006-11-02
IT WORKS AGAIN!!! i didn't have to reinstall at all.  i found a page at 
[http://tim.ultis.net/2006/05/14/cpu-frequency-scaling-unsupported-error-message/](http://tim.ultis.net/2006/05/14/cpu-frequency-scaling-unsupported-error-message/)

with a combination of that and reinstalling powernowd, ubuntu-desktop, and linux kernel headers.  It started to work again.  

Thanks for all your promt help.

---

### Post by neoflight on 2006-11-29
thanks.  reinstalling powernowd worked for me. then add to panel cpu freq scaling and right click..enable governors...and selecting ondemand worked for me...initially i set the freq to 637 Mhz with (userspace in governors) browsing speed got really slow. so just using 'ondemand' now...

cpufreq is not required... while using it i was getting the error something like. "...hardware is either misconfigured or does not support frequency scaling"....

---

