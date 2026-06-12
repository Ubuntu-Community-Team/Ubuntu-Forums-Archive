---
title: "Promise Raid Controllers"
date: 2013-07-08
forum: Hardware
---

### Post by sadams54 on 2013-07-08
I work with a company that I can not name for obvious reasons. This company had a very nice long drawn out tug of war with the Promise company about the RAID controllers. It took a lot of work to get them to admit to it but they finally admitted that thier cards are not, I repeat not hardware RAID. they are primarily used in windows systems and that is what the company I work with used them in. Seems the drivers they supply for windows also includes the software that makes the card perform as a RAID controller.

Those of us in the Linux world have noticed that using the Promise cards is a problem even though they advertise hardware raid. In our world we do not see a single drive as you would expect in a hardware RAID1, instead we see all the drives. I have a Promise tx2300 in a linux system and confirmed what everybody else has seen.

The company I work with dropped Promise technology because they do not have hardware RAID, even though they work in windows systems only. We have removed thier cards from all existing medical systems also. 

Personally I spend a month going in circles with thier tech support that wanted me to do all kinds of things to make it work in linux and MD is the solution which is a software RAID again. 

Basically Promise is selling a plug in hard drive controller and advertising it as a hardware RAID controller. Sounds like a broken promise to me. 

I hope this post helps people having problems with Promise Technology products trying to set up a hardware RAID. bottom line is they will work ok in windows but it is a software RAID not a hardware RAID. It is a mass improvement in the windows world as far as RAID but it is not what they advertise and if you are in a non windows world then please do not waste your money. I have not found a good inexpensive hardware RAID that does not require wiping out current drives to implement.

---

