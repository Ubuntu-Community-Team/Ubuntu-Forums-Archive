---
title: "Question - ATA Security Master Password Revision Code"
date: 2007-10-31
forum: Hardware &amp; Laptops
---

### Post by Jim1 on 2007-10-31
I have googled extensively, read the T13 docs, and tried every thing else I could think of. So this query probably does not have an easy answer unless you are "in the know" about hard disk ATA Security.  

My question is what exactly does the Master Password Revision Code signify?  And how does it get modified?  The very little information gleaned from the aforementioned searches suggest the following facts:
1) The Master Password is not required to be set by the manufacturer.  However, some manufacturers do set this password to a value of their own choosing. (For example, IBM Travelstars seems to be set to one of several initial values, the most common being 32 spacebar characters (20h)).  Whether the manufacturer sets a Master Passord or not, the initial value of the Revision Code (RC) is required to be set to 0xFFFE unless the particular hard drive doesn't support the ATA Security function.  In that case the RC is supposed to be set to 0x0000 or 0xFFFF, if it is available at all.

2) There seems to be no mention in the T13 specs on what the RC was actually planned to be used for. There is obtuse language suggesting that the RC can be used by the IT admin to; 1) verify that the Master Password has not been changed since he/she set it, and 2) that the value of RC currently recorded in the drive can be used to  identify which (of several?) passwords that the admin is using in a project. However, no indication is mentioned at all describing the mechanism by which the RC is changed, much less how is it set to a particular arbitrary value. (One other mention that I found is that the RC can be manipulated to count down, with each change to the Master Password, from the initial 0xFFFE to 0x0, but no clue as to how, or what manufacturer uses the RC in this way.)

If some one out there can rain any information on this topic, I would be particularly pleased as I am at the end of my research resources.

By the way, I must confess that I have "no need to know" nor am I planning any special project which would use this information.  I simply got interested in pursuing the topic after I kept seeing references to the RC and  innocently began to look for more details.

Thanks in advance - and may LINUX (read UBUNTU) be with you always.      -     Jim1

---

