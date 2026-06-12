---
title: "Everything I try to install via apt-get/aptitude gives me a Hash Sum Mismatch error."
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by diablo75 on 2009-05-22
EDIT:  Ignore this post.  I replaced my router...again.  The one that I got which works is a Netgear WPN824 v3.  If your a networking buff, you'll appreciate some of the config settings it offers internally.

It all started when I tried to install skype and virtualbox to my laptop and PC (both are wireless).  I have the medibuntu repositories added so running "sudo apt-get install skype" would normally do the trick.  I've also added the third party sources for virtualbox from Sun's website, so using apt-get to install that should work to.  (As a control, I also decided to uninstall VLC and then reinstall it with apt-get).

All three of these programs (and I suspect this would happen with many more) produce a Hash Sum Mismatch error, after downloading the proper packages completely.  It's acting as if the data is being corrupted along the way but nothing is catching this during the download and requesting a resend of the corrupt packets in the data stream.

So I approached this assuming my router to be at fault.  I started by resetting it (a Netgear WGT624 v3 Wireless G router) to it's factory defaults and then setup a new wireless network with a different ESSID, a different channel/frequency, a different encryption password (WPA2-AES), I even tried it without encryption.  I even tried taking my laptop to the router itself and connecting via the hardlines while disabling the wireless interface.  That still produced the same error.  I was stumped.

Next I bypassed the router and connected my laptop directly to the modem and attempted to install Skype and Virtualbox via a direct connection to the Internet AND IT WORKED.  But the wireless reliability issue still wasn't ruled.  So I took it apart and blew a very tiny layer of dust off the board hoping for the best.  It didn't do the trick.  I would still get the same checksum error if I tried to install via wireless connection.

So I decided to get a new router to see if that would make a difference.  The one I bought is a Netgear WGR614 v9 Wireless G.  Long story short, I still get the same errors when attempting to install anything while connecting to my home router wirelessly.

I don't know what else to try now.  Anyone have any ideas or suggestions?  What are some common ways to troubleshoot a Hash Sum Mismatch error?  I'm looking for AS MANY ideas as possible about this.

---

