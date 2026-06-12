---
title: "How start fresh by format and load latest Ubuntu"
date: 2009-08-30
forum: Installation &amp; Upgrades
---

### Post by tmcd on 2009-08-30
Have an old machine and software on it and I want to start out fresh by formating the entire drive and load the latest recommended Ubuntu.  I tried to research and have myself confused.

_***Hardware***_ ... from November 2007 Everex TC2502 has 512 mg ram, 80 gig hard drive.  Has been gathering dust for over a year.  Long story why and has nothing to do with the machine or software.

_***Software***_ .... has an early original version of g-OS from 2007 on it.  Hated it so loaded various Distros all of which were nicer ... liked Ubuntu (I think the latest I loaded was 7.10).

_***Mess***_ ... was a learning process for me so have fouled up the partitions and did other questionable things because I did not understand then and am a little better now but am still a novice.  I think there is a mess on it.

_***Misc***_ ... I do have the recovery disk but I suspect that it will just reload the early g-OS that did not like in the first place.

_***Question***_ ... I think the best thing to do is format the hard drive and start over .. and immediately load the latest Ubuntu -- hopefully not g-OS.

[LIST=1]
[*]How do I format it?
[*]Any recommendations as to which versions of EXT and Ubuntu would be helpful.
[*]Am I not thinking of anything important?
[/LIST]


[COLOR=DarkOrchid]
Is there a way to do this other than a Sledge Hammer and buying a new PC (ha, ha)? [/COLOR]:lolflag:




Seriously, any advice or help would be most appreciated.

Best regards,
TMCD

.

---

### Post by earthpigg on 2009-08-30
what i personally would do:

boot from a 9.04 live cd.... i would use masonux (see my sig), but i am horribly biased as it is my own Ubuntu-based creation :D. Ubuntu 9.04 Desktop would work great, too, and be the more standard choice.

verify that all hardware works.

click install.

when the option presents itself, select 'manually partition'.

delete all partitions.

create a new partition as type: swap and size: 2gb.

create a new 15 gb partition as ext4.

create a new partition with remaining space as ext4.

give the 15gb partition the bootable flag, and the mountpoint of /. this will be my root partition.

designate the 2gb partition as the swap.

give the last partition the mountpoint of /home. this will be the home partition.


done. finish the install and reboot.

---

### Post by snowpine on 2009-08-30
I agree 100% with Earthpigg's suggestions. If you find them too confusing, you also have the option to choose "Guided install: Use entire disk" and let Ubuntu do it for you.

---

### Post by tmcd on 2009-08-31
Thanks Earthpigg and Snowpine ... 

I appreciate the advice ... 

I will give it a try!

---

