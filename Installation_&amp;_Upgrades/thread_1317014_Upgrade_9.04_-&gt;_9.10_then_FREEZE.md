---
title: "Upgrade 9.04 -&gt; 9.10 then FREEZE"
date: 2009-11-06
forum: Installation &amp; Upgrades
---

### Post by joshuajon on 2009-11-06
I ran the automated update through update manager, everything went smoothly.  Rebooted ok, it lets me login.  Then 5-20 seconds later it freezes completely and that's it.  No recovery, no ctrl-alt-del, nothing.  Anybody have any suggestions?  I thought I was safe with an automated upgrade, but I guess not.  

There should probably be a warning to back up files if there's a possibility that the system will be irrevocably damaged. I'm downloading a disc to do a fresh install, but what a pain.

Anybody?  Anybody?  Bueller?

---

### Post by joshuajon on 2009-11-06
Turns out the same thing happens when I boot from the 9.10 live cd.  WTH?!

---

### Post by apirec on 2009-11-06
I'd say, your system will freeze as well with a fresh installation. You should try to disable desktop effects. That way I got mine at least stable (yet unusable slow!).

---

### Post by joshuajon on 2009-11-06
Isolated the problem: apparently it's related to the netgear wg111v2 usb wireless card.  I can boot up fine with this device unplugged.  When I plug it in it finds the network and then freezes as soon as that's completed.  Hrm...

---

### Post by joshuajon on 2009-11-06
Started a new thread over at the networking forum.

---

### Post by joshuajon on 2009-11-08
Okay, it had nothing to do with networking actually.  The problem was compiz or some other advanced desktop effects.  After disabling desktop effects in GNOME everything worked fine.  Thanks!

---

### Post by michaelzap on 2009-11-08
You might try the latest Release Candidate for the kernel (2.6.32-rc6) as found here:
[http://ubuntuforums.org/showpost.php?p=8263419&postcount=135](http://ubuntuforums.org/showpost.php?p=8263419&postcount=135)

---

