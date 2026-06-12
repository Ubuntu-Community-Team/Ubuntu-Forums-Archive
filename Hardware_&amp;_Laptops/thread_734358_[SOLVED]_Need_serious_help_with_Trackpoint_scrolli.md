---
title: "[SOLVED] Need serious help with Trackpoint scrolling"
date: 2008-03-24
forum: Hardware &amp; Laptops
---

### Post by MountainX on 2008-03-24
I've been using Ubuntu for a couple months now. I have not been able to get my Trackpoint to work correctly and I could really use some help!

Recently I posted this question:
[http://ubuntuforums.org/showthread.php?t=730045](http://ubuntuforums.org/showthread.php?t=730045)

As part of my research I found these two good links:
[http://www.thinkwiki.org/wiki/How_to...the_TrackPoint](http://www.thinkwiki.org/wiki/How_to...the_TrackPoint)
[http://opseast.wordpress.com/2007/11...work-in-linux/](http://opseast.wordpress.com/2007/11...work-in-linux/)

However, my results are not like the results of others. They have success and I don't.

What logs or config files should I examine?

History:
In the default installation of Gutsy on my T61p, the middle button pastes and the TrackPoint scrolling does not work.

I had no file here: /etc/init.d/trackpoint
and I had no config file here: /etc/trackpoint/trackpoint.conf

Next I downloaded configure-trackpoint. The good thing is that it changed the speed and sensitivity settings -- until I rebooted. But it did not address TrackPoint scrolling at all.

configure-trackpoint did create /etc/init.d/trackpoint, but the lines in the file point to the wrong locations. For example, it points to:
/sys/devices/platform/i8042/serio0/serio2/sensitivity
while my actual location is 
/sys/devices/platform/i8042/serio1/serio2/sensitivity
(and not /sys/devices/platform/i8042/serio1/sensitivity as giving at ThinkWiki)

At this point, I don't know what to try next.

References I have already looked at:

Best links:
[http://www.thinkwiki.org/wiki/How_to...the_TrackPoint](http://www.thinkwiki.org/wiki/How_to...the_TrackPoint)
[http://opseast.wordpress.com/2007/11...work-in-linux/](http://opseast.wordpress.com/2007/11...work-in-linux/)

Related links:
[http://www.thinkwiki.org/wiki/Patch_..._configuration](http://www.thinkwiki.org/wiki/Patch_..._configuration)
[http://ubuntu.wordpress.com/2006/03/...tics-touchpad/](http://ubuntu.wordpress.com/2006/03/...tics-touchpad/)

[http://forum.notebookreview.com/showthread.php?t=177638](http://forum.notebookreview.com/showthread.php?t=177638)
[http://ubuntuforums.org/showthread.php?t=711208](http://ubuntuforums.org/showthread.php?t=711208) (Hardy - no solution)

[http://ubuntuforums.org/showthread.php?t=8169](http://ubuntuforums.org/showthread.php?t=8169)
[http://ubuntuforums.org/showthread.php?t=90730](http://ubuntuforums.org/showthread.php?t=90730)
[http://ubuntuforums.org/showthread.php?p=4579287#post4579287](http://ubuntuforums.org/showthread.php?p=4579287#post4579287)
[http://ubuntuforums.org/showthread.php?p=4579268#post4579268](http://ubuntuforums.org/showthread.php?p=4579268#post4579268)


References:
[http://stephen.evanchik.com/taxonomy/term/9](http://stephen.evanchik.com/taxonomy/term/9) developer of TrackPoint driver in Linux kernel
[http://forum.notebookreview.com/show...=186952&page=2](http://forum.notebookreview.com/show...=186952&page=2) (Windows, vmWare)

[http://rsim.cs.uiuc.edu/~sachs/tp-scroll/](http://rsim.cs.uiuc.edu/~sachs/tp-scroll/)

Another place I asked the question:
[http://www.linuxquestions.org/questions/linux-hardware-18/trackpoint-scrolling-not-working-properly-thinkpad-and-ubuntu-630322/#post3099175](http://www.linuxquestions.org/questions/linux-hardware-18/trackpoint-scrolling-not-working-properly-thinkpad-and-ubuntu-630322/#post3099175)

---

### Post by MountainX on 2008-03-24
I just learned about the existence of /var/log/Xorg.0.log. I'm attaching that and my xorg.conf file. 

My problem is that I can't get Trackpoint scrolling to work. Thanks.

---

### Post by MountainX on 2008-03-25
I resolved my problems with help in this thread:
[http://ubuntuforums.org/showthread.php?t=730045](http://ubuntuforums.org/showthread.php?t=730045)

---

### Post by MountainX on 2008-04-04
> **MountainX said:**
> 
References I have already looked at:

Best links:
[http://www.thinkwiki.org/wiki/How_to...the_TrackPoint](http://www.thinkwiki.org/wiki/How_to...the_TrackPoint)
[http://opseast.wordpress.com/2007/11...work-in-linux/](http://opseast.wordpress.com/2007/11...work-in-linux/)


Those links got mangled by copy/paste.

Here is the top one again:
[http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint](http://www.thinkwiki.org/wiki/How_to_configure_the_TrackPoint)

---

