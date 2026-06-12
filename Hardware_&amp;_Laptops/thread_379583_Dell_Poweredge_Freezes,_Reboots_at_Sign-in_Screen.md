---
title: "Dell Poweredge Freezes, Reboots at Sign-in Screen"
date: 2007-03-08
forum: Hardware &amp; Laptops
---

### Post by bondiblue on 2007-03-08
Hi all,
I have been using Ubuntu successfully on a PowerEdge 830 for a few months now.  Recently it froze up and since then I have not been able to boot it up, besides in recovery mode.  When it gets to the sign-in screen, it freezes, and then sometimes it just reboots itself.  Kind of freaky!
I have started it up in recovery mode, but don't know what to look for to try and fix this.

Does anyone have any idea of a starting point.  I'm happy to provide more information, I just don't know what is needed to solve the problem.

Thanks for your help!!!

---

### Post by bondiblue on 2007-03-08
I went through the /var/log/syslog files and found that the last entry after restarting the box is always listed as:

```
apm: BIOS not found
```

After searching around on google, its seems like this may have arisen after I tried to upgrade from 6.06 to 6.10.  Anyone have the same trouble?

---

### Post by bondiblue on 2007-03-08
Grrr... so frustrating.  When the machine is loading, i can ping it and get a response.  As soon as the Ubuntu log in page shows up (after flickering a little bit), the whole screen freezes and then the pings from another machine on the network stop getting through.  Clearly the freeze is not just something with the screen, the whole machine is frozen.

Right now my priority is to just get this thing back up so that a few of the things it was serving up are running so that people in the office can access them (mainly a calendar with important stuff).  How do I just disable the GUI, but not go into recovery mode?

Thanks.

---

### Post by bondiblue on 2007-03-08
I've spent the past 5 hours on the forum and on google, trying to learn what is going on.  My computer continues to not work in after booting up.  After a few seconds at the log-in page, it freezes up.  Sometimes it just reboots itself.

A few questions:

1) What log should one look at to find the culprit of a computer simply freezing up and rebooting for no (apparent) reason?

2) How does one start Ubuntu in "server" mode.  In other words, not with the desktop, but a little more functional than "safe mode"??

3) It is possible to start up under safe mode.  How can i resume all normal services (namely apache, mysql) so that I can serve up my webpages, without invoking the ubuntu desktop?

If I am asking the wrong questions please let me know.

Thanks!

---

### Post by bondiblue on 2007-03-09
Am i asking the wrong questions?  Can anyone tell me where would be a better place to ask?

Thanks!!

---

