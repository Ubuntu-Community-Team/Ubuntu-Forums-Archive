---
title: "Epson XP205 Printer/Scanner, scanner not working"
date: 2013-06-08
forum: Hardware
---

### Post by Camy on 2013-06-08
Hi All
Just installed Ubuntu for the first time, two days ago. Came from Fedora :)
Really enjoying the experience so far. Everything has been quite easy, even though I'm no expert.

The propblem is the all in one scanner won't do its job and scan  :(

I have been looking in the forum and followed some posts, mainly downloading the linux drivers from 
[http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX](http://download.ebz.epson.net/dsc/search/01/search/?OSC=LX)

I am running Ubuntu 12.04 LTS on a 32 bit system
So I downloaded and installed** iscan-data_1.22.0-1_all.deb** first and then** iscan_2.29.1-5~usb0.1.ltdl7_i386.deb**

but it still didn't work. Got some more info from this post: [[COLOR=#0000cd]http://forums.debian.net/viewtopic.php?f=7&t=75889[/COLOR]]("http://forums.debian.net/viewtopic.php?f=7&t=75889")

Then I tried:
[COLOR=#696969]/etc/init.d/saned restart[/COLOR]
got 
*[COLOR=#808080]saned disabled; edit /etc/default/saned[/COLOR]*

I edited /etc/default/saned:
# Defaults for the saned initscript, from sane-utils
# Set to yes to start saned
RUN=no
# Set to the user saned should run as
RUN_AS_USER=saned

Set RUN to **YES**

Then restarted sane with
[COLOR=#696969]/etc/init.d/saned restart
[/COLOR]
Rebooted and it worked. Probably didn't have to reboot, but anyway, it worked.
Thanks to all that contribute.

Hope this post will help someone else!

Cheers!
Solved while asking :)

---

