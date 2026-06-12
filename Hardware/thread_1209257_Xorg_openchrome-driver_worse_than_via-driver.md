---
title: "Xorg: openchrome-driver worse than via-driver"
date: 2009-07-10
forum: Hardware
---

### Post by Kuno81 on 2009-07-10
Hi,

some days ago i tried to install an Ubuntu 9.04 on by Epia M10000.
Everything works out-of-the-box, even the direct rendering. When i started to investigate deeper, i realized, that the hardware acceleration is on (glxinfo says: direct rendering: YES) but glxgears results in 200fps only.
I installed the xserver-xorg-video-via transition package, changed in xorg.conf to the via driver, enabled AGPDMA and got more than 300fps. That was how it is supposed to be! ;-)
For other resons i totaly reinstalled the system yesterday. Now, iam not abled to use the via driver anymore! It's totaly weird. I can install the via transition package... via, via_apg ... modules are loaded but X says "via module doesn't exist". How can that be???? :confused:

I'am looking for either the opportunity to use the "old" via-dirver or to run the openchrome-driver with fully acceleration....

So, there are two questions:

[LIST=1]
[*]How can i/Can i use the old/transitional via driver?
[*]why doesn't work the openchrome-driver properly with the hardware acceleration? The specs says he could use the CLE266 chip, but it doesn't work as good as the "old" via-driver....
did i miss something concerning the settings?
[/LIST]

I hope somebody has experiance with this problem!
Thanks,
Kuno

---

### Post by sanjayak on 2009-11-01
Now the driver name is openchrome.

---

