---
title: "Gsynaptics not working correctly."
date: 2007-01-28
forum: Hardware &amp; Laptops
---

### Post by sirozha on 2007-01-28
After having spent numerous hours on this issue, I got the synaptics driver to work with my intallation of Ubuntu 6.10. I can now control speed of the mouse pointer using the "MinSpeed" and "MaxSpeed" parameters in the xorg.conf file under the "Synaptics Touchpad" section (Section "Input Device", Identifier "Synaptics Touchpad", Driver "synaptics" ...). However, gsynaptics that I installed doesn't have an option to control the mouse pointer speed. Also, I seem to be able to control the vertical and the horizontal scrolling in gsynaptics, but when I change the settings, I see absolutely no change in the xorg.conf file. 

This leads me to believe that gsynaptics doesn't save its settings to xorg.conf file but rather keeps them somewhere else. 

So, my main question is, Is it possible to get the mouse pointer speed to be controlled from gsynaptics rather than by manually configuring the "MinSpeed" and the "MaxSpeed" settings in xorg.conf

If so, could someone provide detailed instructions? Please? I have spent way to much time on this issue.

Thanks!

---

### Post by morehavoc on 2007-01-29
I don't know the answer to that, but I bet that your problem is similar to this other problem that I am having.  When the system reboots, it does not properly find the settings for the touch pad that are saved in the xorg.conf file, but it does after you restart X.  See this thread:
[http://www.ubuntuforums.org/showthread.php?p=207760#post2077607]("http://www.ubuntuforums.org/showthread.php?p=207760#post2077607")
(Synaptics touchpad reverts to default settings after reboot.)

I hope we can figure this out, it is a little frustrating!

---

### Post by sirozha on 2007-01-30
> **morehavoc said:**
> I don't know the answer to that, but I bet that your problem is similar to this other problem that I am having.  When the system reboots, it does not properly find the settings for the touch pad that are saved in the xorg.conf file, but it does after you restart X.  See this thread:
[http://www.ubuntuforums.org/showthread.php?p=207760#post2077607]("http://www.ubuntuforums.org/showthread.php?p=207760#post2077607")
(Synaptics touchpad reverts to default settings after reboot.)

I hope we can figure this out, it is a little frustrating!

Actually, my problem is different. The settings in xorg.conf keep after the reboot. The problem is that the Mouse utility that comes standard with Ubuntu 6.10 doesn't really control anything (or at least doesn't control the mouse pointer speed). However, even after I downloaded and installed gsynaptics, I still cannot control the mouse pointer speed even though other settings (like vertical, horizontal, and circular scrolling as well as the touchpad sensitivity) is controled by gsynaptics. But, I don't see any settings in xorg.conf being changed after I adjust those settings in gsynpatics, and therefore, I believe gsynaptics keeps them elsewhere. By the way, I was able to enable the "tap-off" feature, using syndaemon -d -p -i 1, which works perfectly! So, I guess I'm no longer complaining because I was able to set my mouse up the way I want it to work. However, if I create another account on the laptop for my wife, she would not be able to adjust the mouse pointer speed from gsynaptics, and therefore would have to use the current settings that are stored in xorg.conf. Since she prefers a slower mouse, she would not like that, which makes Ubuntu fail the WAT (wife approval test).

---

