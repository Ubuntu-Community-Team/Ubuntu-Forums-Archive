---
title: "hp nx9420 centrino duo problems"
date: 2007-01-15
forum: Hardware &amp; Laptops
---

### Post by dg88 on 2007-01-15
hey, im kind of new to ubuntu and linux systems  in general, så dont hesitate to ask for more details and preferrably how and where i can find the information.

the problem is that im suspecting my dualcore is not playing nicely along with my less than 2 week old ubuntu edgy installation. the reason is that my system-monitor tool (the gui one with the cool graphs) is telling me that one of my cores are constantly running at 50% even when its only idling. 

another problem is that it takes well over 5 minutes to boot (windows took approx 3 when i had it running alot of startups), i once saw a "boot-graph" but i didnt find out how he got it.

the third problem that i felt the consequenses of just minutes after posting the original post is that the software that keeps track of the battery doesnt work. it show wheter im plugged in with ac or not and the power level i had when i booted the system

i hope atleast one of the people thats browsing this forum can help me or atleast give me some tips

---

### Post by dg88 on 2007-01-23
the duo core seems to work nicely after a reinstallation of edgy aswell as the battery monitor. still no luck on the boot time though

---

### Post by kurosdr on 2007-02-24
The problem with the slow boot has a probable cause: Like most laptops that have an "automatic backup feature" the best and fastest sectors of the disk (the ones that are closer to the edge and spin faster) are occupied by the backup partition (of course, this applies only if you still have the windows partition, and the other factory partition).

Also, another probable cause is the "bad state" problem, that happens in most hp notebooks.

If your laptop doesnt display the Hp logo directly at boot but instead you see a a white dash flashing for some seconds at the top left corner and then you see the hp logo, you re suffering from bad state problems, and see here how to fix it [http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nx9420](http://gentoo-wiki.com/HARDWARE_Gentoo_on_HP_Compaq_nx9420)

---

### Post by dg88 on 2007-05-24
i finally found a probable reason for the long boot time.

i think its trying to auto-config my wireless adapter with an ip-addred (the adapter is named eth1) and might me mistaken for a card with cable. just disabling the wireless card cuts the boot time to where its supposed to be

---

### Post by digitalpure on 2007-05-24
I got everything to run smooth under Edgy, upgrading to Fiesty killed my X and all.  I even tried a clean install.  I love Ubuntu, but edgy is nice and i want to move to Fiesty but getting the X to work for me has been a issue (I am also a noobie).....  I had to go back to XP Pro....

---

### Post by dg88 on 2007-05-31
the upgrade worked nice for me. except the long dl-time everything worked

---

