---
title: "Powernowd delay script, anyone?"
date: 2005-08-21
forum: Hardware &amp; Laptops
---

### Post by eivind on 2005-08-21
I have a HP Pavilion ze5425ea equipped with a 2,66 GHz P4-processor. As we all know, these processors have issues with powernowd/cpufreqd. So when I start it up, i get the message "P4 clockmod intentionally disabled". However, I am able to lower the cpu frequency if i do a

sudo /etc/init.d/powernowd restart

once I have logged in. So I figured it would be nice to execute this command late in the startup process, so I don't have to type this on each startup. I did this:

1. Made a script called p4 in /etc/init.d/, containing these lines:

#!/bin/bash
/etc/init.d/powernowd restart

2. Did a

sudo update-rc.d p4 defaults 99

The script runs okay at bootup, but it seems that it needs to be run _after_ I have logged in, or after the normal bootup.

Could someone help me do this to my script:

1. Put it in the background, so it doesn't interfere with the bootup process
2. Wait some time, say 30 seconds, before executing /etc/init.d/powernowd restart


I think this would do the trick, but I'm not much of a scripter.


Best regards

Eivind

---

