---
title: "Ubuntu freeze: overheating???"
date: 2008-04-29
forum: Hardware
---

### Post by maxclimber1w on 2008-04-29
I have a few problems with my Ubuntu 8.04 installation that have been bugging me for a while. I run a Toshiba U205 
([http://www.notebookcheck.net/Toshiba-Satellite-U200.1520.0.html](http://www.notebookcheck.net/Toshiba-Satellite-U200.1520.0.html))

One of the main problems with this machine is this:

When I leave the computer sitting for a long time (e.g. about 15-20 minutes), the screen goes black, the fan and hard drive seem to be spinning very fast, and the only way to get out is to use shift-alt-sysreq-k and then -r.
This seems to happen more often and more quickly when the computer is at high load, e.g. when I left the comp. last week to upgrade. This is very annoying. I have the machine set to hibernate after about 15 minutes of inactivity but it never seems to get that far.

Is it overheating? Any help much appreciated!

---

### Post by maxclimber1w on 2008-04-30
Can anybody help? This problem sucks, I can't just walk away from my computer without losing everything I am working on.

---

### Post by DandyDon on 2008-05-01
> **maxclimber1w said:**
> I have a few problems with my Ubuntu 8.04 installation that have been bugging me for a while. I run a Toshiba U205 
([http://www.notebookcheck.net/Toshiba-Satellite-U200.1520.0.html](http://www.notebookcheck.net/Toshiba-Satellite-U200.1520.0.html))

One of the main problems with this machine is this:

When I leave the computer sitting for a long time (e.g. about 15-20 minutes), the screen goes black, the fan and hard drive seem to be spinning very fast, and the only way to get out is to use shift-alt-sysreq-k and then -r.
This seems to happen more often and more quickly when the computer is at high load, e.g. when I left the comp. last week to upgrade. This is very annoying. I have the machine set to hibernate after about 15 minutes of inactivity but it never seems to get that far.

Is it overheating? Any help much appreciated!

Suspend / Hibernate doesn't work very well in Hardy. It's a known bug.
I would try using the Power Management settings rather than Suspend.

Although I have a desktop, I'm using the default settings with no problem. I just press the Spacebar, and my monitor powers up, and the hard drive restarts. 

If you are still having problems, test your RAM. Your module my be faulty / failing. A lot of system settings are stored in RAM when unit is powered down.

---

### Post by maxclimber1w on 2008-05-02
This isn't really about hibernate, becuase this problem happens even when the computer is busy and I have disabled the auto sleep/hibernate function, both through power options and with the inhibit applet. Any more ideas?

---

### Post by Bal_Zac on 2008-05-02
If it was overheating, it would usually just shut off, rather than spinning everything up.  You still might want to try this
[IMG]http://www.veiled-chameleon.com/weblog/httpdocs/images/blogcontent/compressed-air.jpg[/IMG]
It works wonders.

Also, setup the system to log to an easily accessible file, let the problem happen, and analyze/post the log.  Good luck.

---

### Post by maxclimber1w on 2008-05-02
How do I set the system to make a log?

---

