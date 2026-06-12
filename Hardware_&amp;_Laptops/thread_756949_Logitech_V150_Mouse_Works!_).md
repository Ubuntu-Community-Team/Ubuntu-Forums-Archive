---
title: "Logitech V150 Mouse Works! :)"
date: 2008-04-16
forum: Hardware &amp; Laptops
---

### Post by SnappyU on 2008-04-16
[[IMG]http://www.logitech.com/repository/192/jpg/2110.1.0.jpg[/IMG]]("http://review.zdnet.com/mice/logitech-v150-laser-mouse/4505-3148_16-31788532.html")
[http://review.zdnet.com/mice/logitech-v150-laser-mouse/4505-3148_16-31788532.html](http://review.zdnet.com/mice/logitech-v150-laser-mouse/4505-3148_16-31788532.html)

After installing ubuntu 6.04, 6.10, 7.04, 7.10 and failing to use the tilt wheel feature of the Logitech V150 Mouse, I finally found the solution in btnx.

Strangely, when I search for v150 on the forums and trying out some of the methods, I found nothing that works.  But btnx works.  :)

Hence this thread, so that v150 users can find the solution easily!! :)

Main btnx thread:
[http://ubuntuforums.org/showthread.php?t=455656](http://ubuntuforums.org/showthread.php?t=455656)

My success post here ... 
[http://ubuntuforums.org/showthread.php?p=4728056#post4728056](http://ubuntuforums.org/showthread.php?p=4728056#post4728056)

> I installed btnx 0.4.9 and btnx-config 0.4.7 on Ubuntu 7.10 and got my logitech v150 mouse working.

Specifically the tilt wheel button, left and right, are working, ie allowing back (alt-left) and right (alt-right) in firefox and nautilus.

**Installation**
As per page one installation.

**Configuration**
I only enabled the settings for the tilt wheel buttons left and right.  All the settings for the other buttons, including scroll wheel forward, back and down are disabled.  This prevents the duplicate keys issue.

**Auto Startup**
I made btnx start up automatically by including it in the session manager  System->Preferences->Sessions

In Sessions->Startup Programs, I click Add, and configured as follows:

Name: btnx
Command: sudo btnx
Comment: Enable support for Logitech Tilt Wheel!

Click OK.

Logged off and on again. Voila, everything is working.

---

