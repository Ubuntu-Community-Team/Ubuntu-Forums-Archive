---
title: "APC UPS Delay Upon Restoration of Power"
date: 2017-11-15
forum: Hardware
---

### Post by webwarriortx on 2017-11-15
Strange switching APC UPS hardware issue. Testing UPS device by cutting power responds as is expected, by switching over to battery backup within milliseconds causing no interuption of power to critical devices. When I restore power to the UPS however, there is a signifcant delay switching from battery backup to utility service power. In addition to the main Linux box that hibernates after automatically sending me a text mesage alerting me to the power outage, I have an NAS drive attached, as well some other critical devices. Once my main server hibernates, the UPS reports over an hour remaining to power low voltage infrastructure, such as for NAS, VOIP (Digital Phone), and smart fire alarms. Restoring utility power results in a significant delay (loss of power) of about 3 seconds, which causes my routers to reboot and my NAS to Check Disk due to improper shutdown (sudden loss of power) thereby defeating the true purpose for having a UPS in the first place. I need to make the UPS switch back to utility power as quickly as it switches from the utility to battery backup, within milliseconds, so as to prevent failure of the NAS and other critical infrastructure due to an interruption of power. I am using Zesty Ubuntu and apcupsd to control the APC UPS.
Thank you in advance to any advice you may have.

Bruce

---

