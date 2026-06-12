---
title: "Canon PIXMA iP1600 print success with Ubuntu 8.10"
date: 2009-01-11
forum: Hardware
---

### Post by newbette on 2009-01-11
since this took me ALL day to get up and running, i wanted to share with other intrepid users out there.  i was able to get my canon pixma ip1600 printer to print using 8.10 with much thanks to vincent cubells:

his solution included the following (among other things): 
-ip2200 driver install
-libxml1 manual install
-sudo apt-get install -f
-ip1800 driver install (DON'T REMOVE ip2200 STUFF!!)
 
the steps are bit convuluted, but if you can follow along with this forum conversation, it works - just don't delete the ip2200 stuff even when you're installing the ip1800 series:

[https://answers.launchpad.net/ubuntu/+source/cups/+question/50742](https://answers.launchpad.net/ubuntu/+source/cups/+question/50742)

---

### Post by jpeddicord on 2009-01-11
Moved to Hardware; tutorials need to be entirely in the post content to be approved, and not just offsite links. :)

---

