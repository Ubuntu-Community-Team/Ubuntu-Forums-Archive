---
title: "External monitor problem"
date: 2011-05-08
forum: Hardware
---

### Post by grabbindrivers on 2011-05-08
Hello,

I posted this in another support category a few days back but I'm reposting this here with more information hoping someone can relate. I didn't specify in my last topic I was using a laptop. Here's the problem:

I'm using an HP dv9617nr,  [specifications are available here.]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01278446&tmp_task=prodinfoCategory&lc=en&dlc=en&cc=us&site=null&key=null&product=3619385")

After much debugging (and around 25 restarts a day) I figured out that after I upgraded to 11.04 Ubuntu no longer detects my display.

Upon digging through my nVidia X server configuration Ubuntu in fact detects the Viewpoint external display I'm using, but I cannot switch the display over to the monitor like I used to. "Applying" the X server settings like I would in 10.10 does not work any longer.

Attempting to fix the problem I applied the nomodeset fix and it didn't fix the problem. I'm experiencing the same problem as most people as well with nVidia cards - the proprietary drivers are installed but according to the driver installer "are not in use".

Can anyone help me? Please let me know if you need to see any logs and I'd be happy to post them. If I can't get this problem fixed in the next few weeks I'm going to go through the painful process of reinstalling and rebuilding my Ubuntu installation I spent so long perfecting. I'd like to avoid that if possible. Thank you.

---

