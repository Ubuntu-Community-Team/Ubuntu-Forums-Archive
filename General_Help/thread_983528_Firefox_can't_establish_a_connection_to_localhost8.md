---
title: "Firefox can't establish a connection to localhost:8080"
date: 2008-11-15
forum: General Help
---

### Post by dctodaylight on 2008-11-15
Hi folks!

Well I'm 90% towards replacing XP with Ubuntu, but have hit a snag...
My Promise RAID card's configuration utility. WebPAM, runs through a web browser.  When I try to launch it, Firefox responds:

Firefox can't establish a connection to the server at intel:8080

If I run the Port Scan in Network Tools, it reports 7 ports that are open, but 8080 isn't among them.So I suspect that I need to open it somehow.  I've done some web searching, and have found others with similar problems, but haven't found a solution...  Most of the posts agree that Ubuntu ships with a firewall that's turned off, but some posts have also said that all ports are closed by default, so I'm not sure which is correct...

Any help would be appreciated!

Dave

---

### Post by dcstar on 2008-11-15
> **dctodaylight said:**
> Hi folks!

Well I'm 90% towards replacing XP with Ubuntu, but have hit a snag...
My Promise RAID card's configuration utility. WebPAM, runs through a web browser.  When I try to launch it, Firefox responds:

Firefox can't establish a connection to the server at intel:8080

If I run the Port Scan in Network Tools, it reports 7 ports that are open, but 8080 isn't among them.So I suspect that I need to open it somehow.
.......

Unless you have installed the Linux version of this RAID software, then no it won't connect because it doesn't exist.

---

### Post by dctodaylight on 2008-11-15
Sorry, should have given a few more details!
This card's driver is native to the Kernel, so I didn't need to do anything there.  I had previously set the card and drives up as a RAID 5 array (in XP), and ubuntu was able to re-partition it, and mount it.  I can read and write to the array, which the system appears to recognize as a four disk RAID5, if I look at the properties.

So functionally it appears ok!  But without the configuration utility working, I'm worried about being able to rebuild it if a drive fails etc...

The WebPAM version I downloaded and installed is for linux, although only Redhat, Fedora & SUSE are officially supported.  

Dave

---

### Post by dcstar on 2008-11-15
> **dctodaylight said:**
> 
........
The WebPAM version I downloaded and installed is for linux, although only Redhat, Fedora & SUSE are officially supported.  

Dave

Then you should do a web search and see if that software runs on Debian/Ubuntu - because that is the issue, I suspect.

I imagine that your have a web server - like Apache - installed and running?

---

### Post by dctodaylight on 2008-11-15
I don't know if my music server software (SqueezeCenter) counts as a web server, in the same sense as something like Apache, but it's running, and working well.  It makes use of some of the other open ports I mentioned earlier.

I'll keep surfing, and will contact Promise support as well...

Dave

---

