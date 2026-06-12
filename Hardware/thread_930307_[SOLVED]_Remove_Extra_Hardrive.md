---
title: "[SOLVED] Remove Extra Hardrive"
date: 2008-09-25
forum: Hardware
---

### Post by adlin5000 on 2008-09-25
What I would like to do is remove an extra 40gig drive so I can use it in another box, but when I do I get errors and my system won't boot.

I have a 500gig Sata, 250gig IDE, and a 40gig IDE hooked up. The 250 is the master and the 40 is the slave on one IDE channel. The 250 is mounted as hda1 and the 40 as hdb1. The 250 has a 1gig swap partition. The rest of the 250 and all of the 40 is ext3.

Any help would be great. If you need more info please let me know.

---

### Post by IcarusR on 2008-09-27
Exactly what errors do you get ??
How far does it get when booting ??

---

### Post by adlin5000 on 2008-09-27
Apparently, I'm an idiot. #-o ](*,)

I just shut down my system and removed the HD so I could get the errors that I was getting. Thats when I realized that the jumper on the 250 was set on master w/ slave present. I changed the jumper to single master and it booted up no problems.

Sorry for taking your time and thanks for the reply. If you had not asked for the error messages, who knows how long it would have taken me to notice the jumper. :roll:

---

