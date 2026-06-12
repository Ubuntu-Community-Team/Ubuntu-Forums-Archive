---
title: "ubuntu is starting to crash more and more often"
date: 2008-08-25
forum: General Help
---

### Post by guine on 2008-08-25
Over the past two or so months I've had an install of fiesty go from having worked very well and never crashing for over a year to crashing more and more regularly.  It doesn't seem to be crashing from me doing any one thing in particular or for me to even be using the computer at the time.  Every time it crashes the caps lock and scroll lock keys start blinking(I have no clue if this means something specific about what is going wrong or if this happens for all crashes).  When I reboot my computer it takes longer to boot up and when it reaches the graphical boot screen with the progress bar it just sits there for a little and then switches to a show text while it boots(it doesn't do this normally) and I get two messages saying "file system not clean" as it is booting(I think this is when it is scanning my harddrives, which I have two of).  Any ideas what is wrong with my computer and how to fix it?  Thanks.

---

### Post by xeth_delta on 2008-08-26
> **guine said:**
> Over the past two or so months I've had an install of fiesty go from having worked very well and never crashing for over a year to crashing more and more regularly.  It doesn't seem to be crashing from me doing any one thing in particular or for me to even be using the computer at the time.  Every time it crashes the caps lock and scroll lock keys start blinking(I have no clue if this means something specific about what is going wrong or if this happens for all crashes).  When I reboot my computer it takes longer to boot up and when it reaches the graphical boot screen with the progress bar it just sits there for a little and then switches to a show text while it boots(it doesn't do this normally) and I get two messages saying "file system not clean" as it is booting(I think this is when it is scanning my harddrives, which I have two of).  Any ideas what is wrong with my computer and how to fix it?  Thanks.

It can be a number of things, starting from misconfiguration and in the worst case some hardware problem.

The LEDs blinking, seem to suggest to me a kernel panic, if I recall correctly.

When a system is turned off, the partitions are first unmounted, so that their integrity is ensured. When a crash occurs, a restart or a shutdown happen without unmounting the partition.
What you are seeing (as a longer boot) is most likely the system just performing a file system intergrity check at least for the / partition.

Now, regarding the crashes, have a look at /var/log/syslog
Anything there that can suggest a problem? Post the output.

---

### Post by Oldsoldier2003 on 2008-08-26
Since this post doesn't appear to be Apple Specific I'm moving it to General Help for more exposure.

---

