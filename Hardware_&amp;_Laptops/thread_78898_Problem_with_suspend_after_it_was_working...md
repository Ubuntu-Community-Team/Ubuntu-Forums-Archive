---
title: "Problem with suspend after it was working.."
date: 2005-10-19
forum: Hardware &amp; Laptops
---

### Post by jmcvey on 2005-10-19
Hoping someone can help me out. I've an IBM R50p laptop that was working fine regarding suspend. Worked whether I hit the sleep button combo (Fn-F4) or closed the lid (the latter after I changed what lid.sh to be a copy of the sleep.sh). Was going through the Add Applications to see what else is out there and saw Power Preferences that looked like it could be used to setup the laptop to do some other things like suspend after a set timeout and such. This seemed great so I installed it. Well, it installed without issue, but it also provided no functionality (I literally had no options I could choose from to configure it and the info on it said it would display whatever features from my hardware were available). Since it didn't seem to add anything I uninstalled it. That's when I noticed that suspend doesn't work via the lid closing anymore. I know get just the screen being turned off. I double checked the scripts and everything is still the same (I even ran the scripts and they work). Even the logout 'Suspend the computer' works as it should. Just the lid closing doesn't work.

Any ideas on where else I should look or even what I should re-install to regain the lid working correctly?

Jer

---

### Post by jmcvey on 2005-10-19
Okay.. strange but it's now working as it should. I tried reinstalling the Power Management software first. It still doesn't provide any options to configure it so once again I removed it. This time, though, I an appointment and would be gone for several hours. I powered off the laptop figuring I'd work on this later. Get back, power it back up, phone rings so I close the lid and run to get it. Expecting the laptop to be on when I get back I was surprised to see the little "sleep" LED on and the laptop powered down. Opened the screen and it restores as it should. Thinking maybe going into suspend was just taking a longer time now I close the lid again and within a few seconds I've got the "sleep" LED glowing and the laptop powered off.

I've no idea what glitched the first time with that power management software's uninstall but it looks like repeating the process cleared everything up. I'd still be curious if there's other places to check for acpi or sleep settings other than the usual (i.e. /etc/default and /etc/acpi as all the scripts and files appeared to be normal and correct). Any ideas welcomed.

Jer

---

