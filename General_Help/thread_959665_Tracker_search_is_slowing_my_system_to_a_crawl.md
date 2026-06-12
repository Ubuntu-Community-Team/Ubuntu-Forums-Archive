---
title: "Tracker search is slowing my system to a crawl"
date: 2008-10-26
forum: General Help
---

### Post by wheezer on 2008-10-26
I'm runnning Hardy on a duo core machine.

For past 2 weeks, Tracker is simply bringing my system to its knees whenever it starts indexing.   It consumes so much CPU, the desktop cannot even draw.  Only killing the process will recover anything.  I've tried Admin >Preferences > Search and Indexing, and changed it's performance to slowest, but the problem comes right back a few minutes later.  I've read on launchpad that this was a bug over a year ago. I cannot believe it still is.

Can anyone suggest a fix for this?  Should I reinstall it, or something?  If I completely disable it, will Beagle still work? I cannot figure out which search is "native" to ubuntu, since they both seem to come installed.  Do they share an index? Clarification here would also be helpful.

Thanks.

---

### Post by exploder on 2008-10-26
Go into "Sessions" and take away the check for "Tracker" and "Tracker Applet" and you should be in good shape. Tracker tends to slow thing down so this is how I eliminate this problem.

---

### Post by lswb on 2008-10-26
If you want to try tweaking it before disabling completely, try adjusting the settings from 
Main Menu/System/Preferences/Searching and Indexing. 

(or from cli use  "tracker-preferences" )

---

### Post by wheezer on 2008-10-27
> **lswb said:**
> If you want to try tweaking it before disabling completely, try adjusting the settings from 
Main Menu/System/Preferences/Searching and Indexing. 

(or from cli use  "tracker-preferences" )


Thanks. But what do I change?  I cannot believe that the "slowest" setting would still eat all my CPU. It must be a bug, as reported last year.  I really want indexing of some kind. Does beagle have its own indexes, or are they shared?  This is just so nasty. It's the kind of problem I don't have on my windows platform.  As much as I appreciate what they have done, I wish the developers would stop adding gee whiz features to Ubuntu, and focus on the basics.  It's going on quite a few years now, and the "promise" is still kinda iffy.

Thanks for help

---

### Post by wheezer on 2008-10-27
> **exploder said:**
> Go into "Sessions" and take away the check for "Tracker" and "Tracker Applet" and you should be in good shape. Tracker tends to slow thing down so this is how I eliminate this problem.

Exploder, what do you use for search, then?  I find it hard to believe that tracker woudl be designed to gobble almost all available resource.  Might reinstalling it fix anything?

---

