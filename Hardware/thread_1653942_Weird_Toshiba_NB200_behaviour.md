---
title: "Weird Toshiba NB200 behaviour"
date: 2010-12-27
forum: Hardware
---

### Post by GuiGuy on 2010-12-27
My 18 months old Toshiba NB200 has been running ubuntu since the day I got it. It only has Ubuntu installed. 

I upgraded to Maverick a few days back. SInce then the computer stops processing every few seconds. It can be made  to start again for a few more seconds if a key is pressed or mouse button is clicked. It will also do this during downloading. So, for example if I am doing sudo apt-get upgrade I'll need to continuously click the mousebutton to coax the computer into ongoing action until the upgrade task is completed. This is not convenient when there are 182M worth of updates waiting. 

Anyone have any idea what might be happening or should I suspect the self destruction mechanism that seems to be built into all modern appliances and set to trigger shortly after the warranty expiry?

Cheers

---

### Post by GuiGuy on 2010-12-27
Fixed: In BIOS there is a configuration for the CPU optioned as "dynamic". Disable it.

---

### Post by Fourcultures on 2011-01-12
Interesting that this worked for you, but the dynamic mode can be useful. Another fix for the 'weird' behaviour with maverick is at 
[http://ubuntuforums.org/showpost.php?p=10199447&postcount=244](http://ubuntuforums.org/showpost.php?p=10199447&postcount=244)

Should you try it, please let me know if it worked.

---

### Post by GuiGuy on 2011-01-12
> **Fourcultures said:**
> Interesting that this worked for you, but the dynamic mode can be useful. Another fix for the 'weird' behaviour with maverick is at 
[http://ubuntuforums.org/showpost.php?p=10199447&postcount=244](http://ubuntuforums.org/showpost.php?p=10199447&postcount=244)

Should you try it, please let me know if it worked.

I have noticed that since disabling "Dynamic" the battery stays charged when the unit is powered down, whereas previously it would deplete over a period of about 48 hours. So that's been a bonus in a way. 

But I'll try those kernel parms and will let you know. Thanks for the tip

Cheers

---

