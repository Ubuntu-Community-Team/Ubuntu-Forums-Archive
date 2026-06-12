---
title: "goal: install phpbb3.  why xampp / lamp when I have mysql and php?"
date: 2009-01-06
forum: Installation &amp; Upgrades
---

### Post by bosworthy on 2009-01-06
Can someone tell me why I need to install xampp on ubuntu?  I went to synaptic and got mysql and php installed.  I went to [http://localhost](http://localhost) and it said "it works."  Where is the folder where I can my html files?

My goal is to install phpbb3 which requires mysql and php, which I already have.  I only see phpbb2 in ubuntu and not phpbb3.  

I did go here: [http://ubuntuforums.org/showthread.php?t=976550](http://ubuntuforums.org/showthread.php?t=976550)  but it doesn't seem to have answers to my questions.
I read it more carefully and think this helps:

"Installing LAMP is easy. Go in System > Administration > Synaptic, under edit select 'Mark packages by task. Then select the LAMP server and you are done."


Synaptics doesn't show LAMP as some people say it would be there.  Please advise my next step.



Thanks.

---

### Post by jken146 on 2009-01-07
To install the whole LAMP server, type ```
sudo tasksel install lamp-server
```

The default directory for the files that Apache2 serves is /var/www.

More info: [https://help.ubuntu.com/community/ApacheMySQLPHP](https://help.ubuntu.com/community/ApacheMySQLPHP)

---

### Post by bosworthy on 2009-01-15
Thanks Jken,

I've installed the LAMP servers shortly after I posted by going into the Synaptic Package Manager -> Edit -> Mark Packages by Task.  Rebooted, but I don't see the logon as described here (middle of the page, see attach).

[http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html](http://www.ubuntugeek.com/ubuntu-710-gutsy-gibbon-lamp-server-setup.html)  

Note that I did not install Ubuntu according to the above, what I did was to install via the livecd.

Is there a site that kind of get me grounded on this LAMP server thing?

Thanks.

---

