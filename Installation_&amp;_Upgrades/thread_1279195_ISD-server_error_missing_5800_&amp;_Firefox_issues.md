---
title: "ISD-server error missing 5800 &amp; Firefox issues"
date: 2009-09-30
forum: Installation &amp; Upgrades
---

### Post by lasleym on 2009-09-30
I'm not sure how much history to put on here as its my first post, so please bear with me.  I have limited knowledge, but I can read, and that sometimes gets me into trouble (as now).

I installed Ubuntu 9.04 on our PC after wiping the HD clear of Windows.  In my excitement of new programs, I also installed the education desktop, which I believe also gave me a Kubuntu desktop.  Some things have been buggy, like the past two days when Firefox 3.5 would only load once and refuse to if closed per restart. [**EDIT** - this hasn't happened again, and we've changed motherboards and are now running 9.10.]

While trying to see where this problem existed, I logged onto a different session, something I hadn't done before, and I began to get the ISD-server error port 5800.  This was under the GNOME or X session **not **KDE, where everything worked fine.  

I found this [forum]("http://kubuntuforums.net/forums/index.php?topic=3093025.0") and tried various things in different sessions, finally finding the root terminal.  I was able to see the problem port using the 'ps aux | grep ica' command but not fix it permanently with the 'kill all -9 ica' command.  

So, I tried the 'apt-get remove isd*' command **and continued with yes**.  

So, now of course, I have removed many things which I did not want to do and I would **love** some assistance in righting my mistakes.  Help please and thank you.

I am currently running ubuntu 9.04 off the live CD and backing up my files (again).

EDIT:  After going through this (gcompris freezing and ISD-server error) a few times, I found [another thread]("http://answers.launchpad.net/unbuntu/+question/46259") that explains what happened better.  

**The fix**:
It's Edubuntu.  

1. Check system monitor for "ica"
2. Kill/end all processes including the ica-luancher

From Thomas Kluyver (9/29/08) on [http://answers.launchpad.net/unbuntu/+question/46259](http://answers.launchpad.net/unbuntu/+question/46259) it's from a package called "italc-client" which is installed as part of Edubuntu.  

Also try:  'netstat -pant' and look for a program listening to port 5800.

---

### Post by lasleym on 2009-10-01
I just reinstalled ubuntu, picked the right education software package (so now I've got the edubuntu desktop choice and login).  

If anyone reads this, I would love to know how to fix the ISD-server error, that was quite annoying.

---

### Post by arpanaut on 2009-10-01
This may help if you just want to get rid of the error message... 

[http://ubuntuforums.org/showthread.php?t=786355&highlight=ISD-server+error](http://ubuntuforums.org/showthread.php?t=786355&highlight=ISD-server+error)

---

