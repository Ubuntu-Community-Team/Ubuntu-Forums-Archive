---
title: "Problem Connecting With Dialup Modem in Ubuntu 7.10"
date: 2008-01-12
forum: Hardware &amp; Laptops
---

### Post by blackhole82 on 2008-01-12
I have not had much luck getting a connection with dialup.  I tried using a winmodem and couldn't get it to work, so I now am trying a hardware modem since I heard that they work better and don't require drivers.  The modem I have is on the list of modems that are supposed to work with Linux.  However, I'm getting the same error I did with my winmodem.  I can dialout but when I get to the login stage and my username and password is being authenticated I get "request denied".  It appears that the modem is working since I can dialout, but there is some minor detail I'm overlooking.  It kind of seems like it's a problem on the ISPs end.  I'm using basicisp and it's supposed to be Linux friendly so I don't get it.  Does anybody have any suggestions or pointers for my particular situation?

---

### Post by uNoobuntu on 2008-05-01
I realize this is an old thread, but I figured I'd post with some experience using basicisp.net on Linux. Our client was, however, using Redhat.

Try putting "Stupid mode = 1" into the bottom of the /etc/wvdial.conf file, then run a connection.

---

