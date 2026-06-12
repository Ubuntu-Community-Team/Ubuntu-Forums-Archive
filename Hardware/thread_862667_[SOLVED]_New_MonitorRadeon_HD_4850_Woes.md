---
title: "[SOLVED] New Monitor/Radeon HD 4850 Woes"
date: 2008-07-17
forum: Hardware
---

### Post by blackhole82 on 2008-07-17
I've been beating my head against a wall for two days now trying to get my new radeon card to work with a new monitor.  I've followed a couple different guides on installing the proprietary ati drivers.  I've installed and uninstalled numerous times without much luck.  On my latest attempt the login screen actually has what appears to be a decent resolution.  However when I login I just get a blank white screen now.  I'm stuck.  Is there anybody that can help me out?  I think I understand now why I heard people in the past say ati was hell in linux.

---

### Post by markbuntu on 2008-07-17
What is your new monitor?
Did the card work before you did this??
Did you use the Catalyst Control Center to detect the new display?
Or did you not even get that far?

Did you try 

sudo dpkg-reconfigure -phigh xserver-xorg

from recovery mode to reload x so it can autodetect?

We need more information.


Did you use this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

As far as I know, it is the only one that 4850 owners have used successfully. This card is supported by the 8.6 driver and other people have successfully got it to work so do not despair.

---

### Post by blackhole82 on 2008-07-17
> **markbuntu said:**
> What is your new monitor?
Did the card work before you did this??
Did you use the Catalyst Control Center to detect the new display?
Or did you not even get that far?

Did you try 

sudo dpkg-reconfigure -phigh xserver-xorg

from recovery mode to reload x so it can autodetect?

We need more information.


Did you use this guide:

[http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide)

As far as I know, it is the only one that 4850 owners have used successfully. This card is supported by the 8.6 driver and other people have successfully got it to work so do not despair.

My new monitor is an Acer AL2216W LCD that is 22".  I want to be able to run it at the standard 1680 X 1050 resolution.  I got the card and monitor at the same time, so I haven't had the card working yet with driver acceleration.  When I first started attempting the driver installation process I was booting into low resolution mode.  I haven't gotten to the point of using catalyst to detect my display. The main problem I was having was that after I installed the driver and ran fglrxinfo it was still listing MESA instead of ATI. The guide you listed is one of the one's I followed.  There is another one very similar to it.  I will try that command you showed me to reset X.

---

### Post by blackhole82 on 2008-07-17
Well I figured out what was wrong.  I followed the guide exactly and unchecked the use restricted driver for ATI.  That's why it wasn't showing up.  When I reconfigured X and then decided to check use restricted driver I was able to configure everything from Catalyst.  I feel dumb now :/

---

### Post by markbuntu on 2008-07-17
OK, great. Please mark this thread as solved.

---

