---
title: "New install after virus, hardware issues."
date: 2011-02-25
forum: Hardware
---

### Post by Mazzelsha on 2011-02-25
Just wondering if someone could offer some advice, my godfather's computer is running latest version of ubuntu & the other day it froze & appeared to have a virus. We tried to format the existing hdd & reinstall ubuntu but it kept hanging & then came up with an error message stating that it was unable to completely format the drive & install ext4 partition. So I fitted a new hdd & ubuntu installed perfectly & everything seemed to be running fine. 

However, he's just advised me that the computer had switched itself off & wouldn't come back on. I tried to restart it but eventually had to remove the cmos battery which seemed to fix the power button but then we had an error message on start up saying that the temp folders weren't loaded correctly. After restarting again we now have it running but the this last time the new hdd was making a grinding noise - which has now stopped completely. 

There is a lot of dust in the casing which I've tried to clean out, but I'm wondering whether it's a virus that's spread via the motherboard, the cmos battery is dying or the new hdd is dying. Could anyone point me in the right direction please?

---

### Post by TuxIsAwesome on 2011-02-25
Your HDD is most likely dying, the grinding noise tells me that much, even though it has stopped for the time being.

Can you boot into a 10.04+ Live CD and check it's health via Disk Utility, assuming it supports S.M.A.R.T. 

You also might as well replace the CMOS battery, as you had to remove it originally to get it to boot. I bet it either A. Has a Weak Charge, or B. Is dead.

I highly doubt it was a virus, I haven't run into one yet on any Linux OS.

---

### Post by Mazzelsha on 2011-02-25
will try to boot from the live cd tomorrow morning & see what happens, will update here once I've done that. Thanks for the quick reply :)

---

### Post by Mazzelsha on 2011-02-27
ok, battery is definately dying, power keeps going out & only way to start it is to remove the battery & then pop it back in. So, off to buy a new one. Thanks for your help :)

---

### Post by poodoopealeoaph on 2011-02-27
It most likely isn't just the battery though. If it says that it can not completely format then the other person above me was right. The hdd is most likely on it's way out. You should try to use an old hdd you may have lying around and see if it installs correctly. It should.

by the way though.... "there are so few viruses for ubuntu linux that they are considered to be non existent. Even when one is created, the programmers change code for the parts of the system that the virus effects. So, the virus will be obsolete promptly after creation." - Canonical

---

### Post by Mazzelsha on 2011-03-10
Further problems with this have now arisen, the computer just froze last night & the firefox screen turned grey. Finally got it to respond & it allowed me to minimize the screens open but then froze again. Tried to reboot & it comes up saying 'read error'. In light of the previous problems has anyone got any ideas on this or could point me in the right direction please??

---

### Post by mikewhatever on 2011-03-10
Have you checked the disk health with the Disk Utility as asked in post #2?

---

### Post by Mazzelsha on 2011-03-10
yep, it said it was fine. I've opened up the casing as I could hear the grinding noise again & this is apparently coming from the main fan (not CPU fan) could this be causing the problem? Sorry, I'm probably be really dumb on this one!

---

