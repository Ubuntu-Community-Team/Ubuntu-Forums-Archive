---
title: "870k+ load cycle count on WD green drives"
date: 2011-09-26
forum: Hardware
---

### Post by iverasp on 2011-09-26
Hi. While looking for info on what drives to buy next for my fileserver I found a neat little surprise. The WD green drives are so green they are parking the heads so often their lifetime can easily be reduced to less than a year. Checking my two 1Tb WD drives I see the "Load/Unload Cycle Count" has a value over 870 000 (each) after running for just over a year. They have a minimum rating of 300 000 for a lifetime...

How alarmed should I be? I was going to upgrade the server with another 1 Tb drive but it seems I should get three new drives and replace the WD green ones? After doing so, can they still be used for anything or should they be tossed?

They are currently in a raid5 setup with two other drives. I trust that the raid-array could be rebuilt if one green drive dies, however, with the other one being at the verge of death, can I still sleep well at night?

---

### Post by iverasp on 2011-09-26
Found more info if anyone is interested:

"the drives are designed to be good for 1 million parks"
apparently, although my retailer stated 300k. I do not know for sure.

Seems it will be sufficient to disable "IntelliPark" with WDidle3:
[http://www.synology.com/support/faq_show.php?lang=enu&q_id=407](http://www.synology.com/support/faq_show.php?lang=enu&q_id=407)

and hope the drives won't fail shortly after 1 million parks.

This guys drives have reached 1.3 million parks, still working fine
[http://forums.whirlpool.net.au/forum-replies.cfm?t=1351539&r=22139577#r22139577](http://forums.whirlpool.net.au/forum-replies.cfm?t=1351539&r=22139577#r22139577)

I'm just going to let them be in the raid5 array and hope all works out in the end.

Lesson to be learned: if buying WD green drives, disable IntelliPark at day 1 and live happy

---

