---
title: "4K60 on Ubuntu 19.04"
date: 2019-06-17
forum: Hardware
---

### Post by cliffflip on 2019-06-17
Hi, I just want to know whether my XFX RX 550 4GB GPU supports 4K 60fps on Ubuntu 19.04. Right now the maximum refresh rate I can set is 30hz (on 4K resolution), and if I go beyond that (to 60hz), the screen goes blank with no countdown to reverse the setting, then I have to force restart my PC.

I'm using built-in driver from the OS as official AMD driver only supports Ubuntu 18.04. Please help, thanks in advance.

[http://www.xfxforce.com/en-us/products/amd-radeon-rx-500-series/rx-550-4gb-rx-550p4sfg5](http://www.xfxforce.com/en-us/products/amd-radeon-rx-500-series/rx-550-4gb-rx-550p4sfg5)

---

### Post by CatKiller on 2019-06-18
It says it's got HDMI 2.0 and DisplayPort 1.3, so it should do. You haven't said what monitor you're using (some early monitors could only do 4K30), or what connection you're using (HDMI 1.4 can only do 4K30).

---

### Post by cliffflip on 2019-06-18
Hi CatKiller and thanks for your reply.

My monitor is Samsung U28E590D. It has 1 DP and 2 HDMI ports. I also use the monitor for my Windows PC, and there&#8217;s no issue displaying 4K60 from Windows (GTX 1070) through DP and both HDMI ports. I&#8217;ve tried connecting the RX 550 through either HDMI ports and I can&#8217;t get past 30hz. I haven&#8217;t try DP though, as the DP port occupied by Windows and it&#8217;s currently in use.

---

### Post by CatKiller on 2019-06-18
One of the HDMI ports definitely won't work, since it's HDMI 1.4. The 2.0 one should, as should the DisplayPort one. I would double-check it specifically with the HDMI 2.0 port, and, if that doesn't work, try the DisplayPort one temporarily. If none of them work, hopefully someone will be able to find you a modeline or tweak to use.

---

### Post by cliffflip on 2019-06-19
I can confirm 4K60 works with DP port, I even switched to my older GPU (R7 260X) and it also works!

Thanks CatKiller

---

