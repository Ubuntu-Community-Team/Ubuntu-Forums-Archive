---
title: "xorg config file 3 heads"
date: 2015-08-02
forum: Hardware
---

### Post by Chris_Boley on 2015-08-02
Greetings. I have a strange issue>
Advanced Micro Devices [AMD] nee ATI Radeon RV250 [Mobility FireGL 9000] (rev 02) <== two heads <<<  Both being used
VGA compatible controller: NVIDIA Corporation NV34 [GeForce FX 5200] (rev a1) << First head only being used.

HP compaq LA1951g Monitors. Successfully have all 3 monitors up and running in xinerama mode but second head on Radeon card won't go past 1024x768 res. I'd like to post xorg.cfg file:
[http://pastebin.com/Gcwp0EVK](http://pastebin.com/Gcwp0EVK)

Please excuse me if the pastebin link is contradictory to forum rules. I was kind of hasty and didn't read the rules.  I apologize. Any insight into adjustments I could make on the cfg file would be awesome. Thanks

Chris

---

### Post by Chris_Boley on 2015-08-02
You may mark this as solved. As I figured it out myself. My monitor designations in my "device" section were incorrectly marked. 
Thanks.

---

