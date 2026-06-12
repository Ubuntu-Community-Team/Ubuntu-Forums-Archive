---
title: "Scrolling Trackpoint T400 Intrepid"
date: 2008-11-05
forum: Hardware
---

### Post by udbhav on 2008-11-05
I can't seem to get my middle button to scroll in conjunction with my trackpoint.  I followed the instructions found below and created /etc/hal/fdi/policy/mouse-wheel.fdi.  I restarted hal and gdm, to no avail.  Am I missing something?

[http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Scrolling_with_Trackpoint]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_(Intrepid_Ibex)_on_a_Thinkpad_T400#Scrolling_with_Trackpoint")

---

### Post by m_l17 on 2008-11-06
I made that file, rebooted and works for me on my T21. I didn't have to make any more modifications, it just works with Firefox, terminal etc... :)

I did use this:

[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#TrackPoint_under_Ubuntu_8.10_using_HAL]("http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint#TrackPoint_under_Ubuntu_8.10_using_HAL")

It varies a bit from the one you posted. Maybe try that one out and or do a reboot.

Thank You for posting this, I forgot to do in my resent install of Xubuntu.

---

### Post by udbhav on 2008-11-06
Resolved!  Thanks.

---

### Post by m_l17 on 2008-11-06
Great :) I'm curious how did you get yours to work?

---

