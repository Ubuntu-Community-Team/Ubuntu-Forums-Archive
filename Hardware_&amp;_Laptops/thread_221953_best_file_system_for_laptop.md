---
title: "best file system for laptop"
date: 2006-07-24
forum: Hardware &amp; Laptops
---

### Post by Orion2000za on 2006-07-24
from a mailing list I was told that EXT3 has a "flush" function that makes it basically never stop spinning, thereby making it most unsuitable for laptop use (eating battery life). 

I am not techie enough so I ask for opinions on this - is it true and if so will not the "laptop-mode" somehow disable this? 

Cause if it IS true then one should of course use other filesystems for laptop use such as ext2 or Reiserfs....

Cheers,
Orion

---

### Post by djoelsson on 2006-07-24
Hi,  I use ext3 on my laptop and I haven't noticed this at all.  Do you have a source for that information?

In my case, battery life is almost completely determined by processor speed and wifi usage.

---

### Post by reacocard on 2006-07-24
I've never noticed it either. And actually, it's better if the harddisk doesn't stop spinning. Starting it back up takes a huge amount of energy compared to just leaving it spinning. Only if the computer's going to be idle for a long time does it make sense to turn off the harddisk. laptop-mode has options to control both harddisk spindown and the ext3 flush.

---

### Post by Orion2000za on 2006-07-25
Well let me try and fnd the source, it is a thread on a mailinglist on another PC so will take a bit of digging. But if you say that laptop-mode has controls for this behaviour then the problem seems a bit academic. Just heard from another guy though that his laptop similar to mine runs +2hrs in ubuntu and mine runs up to 3.5 hrs in XP. Lots of stuff that can have an impact there of course, such as an ageing battery and what you do etc etc

---

### Post by Orion2000za on 2006-07-25
> **reacocard said:**
> I've never noticed it either. And actually, it's better if the harddisk doesn't stop spinning. Starting it back up takes a huge amount of energy compared to just leaving it spinning. Only if the computer's going to be idle for a long time does it make sense to turn off the harddisk. laptop-mode has options to control both harddisk spindown and the ext3 flush.

found it, here comes a long quote;
ext3 is the problem with your disk.  It uses a forced-flush interval of
about 30 sec IIRC.  In other words, regardless of what is or isn't going
on, the ext3 driver forces a sync and hence the hard drive never goes to
sleep (neither would you if someone poked you in the ribs every 30
seconds!).

Solution, unfortunately, requires reformatting ALL the ext3 partitions
with something else.  I'd suggest reiserfs as, like ext3, is a
journaling file system and is quite mature.  I can't remember if jfs and
xfs use the same "fixed sync interval" fru-fru like ext3 though, so I'll
hold short of recommending them.
source James Gray on Kubuntu mailing list

Orion

---

