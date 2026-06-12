---
title: "Broadcom Corporation BCM4306 how to turn on wifi"
date: 2010-02-21
forum: Hardware
---

### Post by Bniewo on 2010-02-21
I have Broadcom Corporation BCM4306 wifi card in my laptop and it works fine. However, when I close my laptop it disables my wifi and I don't know how to turn it back on without restarting. Any help or key commands to turn it back on?

---

### Post by quixote on 2010-02-23
Do you have the network-manager-applet running in the notification area?  It's usually a set of bars showing signal strength, somewhere near the volume control.  If not, the first thing is to get that turned on.  Right-click on an empty part of the panel, and select "Add."  You want to add the applet called "notification area."  That adds a bunch of stuff, but unfortunately there's no other way to get the icon you want.

Once you've got it, when you lose wireless for no reason like that, it usually helps to right-click the icon, untick "enable wireless" and then tick it again to enable wireless.  That generally kicks it into action again.

If that doesn't work, you can configure your /etc/network/interfaces file, but let's wait to worry about that until we need to.

---

### Post by AlexZaim on 2010-03-05
try these
[http://ubuntuforums.org/showthread.php?t=1408333]("http://ubuntuforums.org/showthread.php?t=1408333")

[http://ubuntuforums.org/showthread.php?t=283667]("http://http://ubuntuforums.org/showthread.php?t=283667")

---

### Post by quixote on 2010-03-05
The second link is broken.  It should be: [http://ubuntuforums.org/showthread.php?t=283667](http://ubuntuforums.org/showthread.php?t=283667) (Trust me, the underlying url is different. :D)

---

