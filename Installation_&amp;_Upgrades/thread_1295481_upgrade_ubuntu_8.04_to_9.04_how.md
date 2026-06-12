---
title: "upgrade ubuntu 8.04 to 9.04 how?"
date: 2009-10-19
forum: Installation &amp; Upgrades
---

### Post by awayguy on 2009-10-19
Halo

I,ve got now a 8.04 ubuntu hardy heron 64bit version on my laptop. now i want upgrade to 9.04, well i have no idea how to. and when i,m booting the laptop there are more than 10 various old kernel versions to choose. is there a possibility to remove them? sorry people i,m a beginner. once i installed this old version, and installed some other stuff, like tablet input and other stuff. i worked on two platforms on windows and ubuntu, but i used more of the time windows. but now i want stay most of the time on ubuntu for sure.
now i think i need the assistance of this forum :D

with regards

---

### Post by awayguy on 2009-10-19
ok i see it

---

### Post by bulldog on 2009-10-19
I don't think you can upgrade from 8.04 to 9.04 you should first go to 8.10 and then 9.04.

If I may give you some advice,wait for a few days,9.10 is the new release,and do a fresh install,instead of an upgrade.

You can download the 9.10 beta live cd and try it out on your hardware,to see if everything is functional.

---

### Post by awayguy on 2009-10-19
ok then let us analyse this case: 
i've got on a 200gb harddisk two partitions. one: 135gb with vista. other one 48gb with ubuntu. and there is also this windows vista partition which is always there (to reinstall vista)
now let us think, i want to work a lot with ubuntu. would i be better to belay maybe 100gb with ubuntu and remove this "secure vista partition".
as I remember you can choose while installing ubuntu, how much space it should belay on the harddisk. and there i have also the posibility as a student, to install windows7 for free.
so now would it make sence to remove this "20gb emergency vista partition" or just let id because i dont need as much space and install on 80gb win7 and on 80gb ubuntu 9.10 ?

---

### Post by bulldog on 2009-10-19
I should decrease Vista as small as you can get **using the disk management utility build within Vista** so you will be sure your Vista will not be damaged by this action.
Defrag one or two times before you do so.

Next step.
Let's assume Vista will be decreased till say 100GB.
let the recovery partition as it is,
Now you'll have about 80GB space.

Create in this free space an extended partition about 12GB
Make a logical partition in the extended partition 10GB for /  [system]
Make a logical partition in the extended partition from the rest of the space 1-2GB for swap
Create a primary partition from the rest of your space 68GB give or take a few MB's, for a /home partition.

If you understand what I'm talking about we can go with a possible install
and the mount points.
If not,just ask your questions.

---

### Post by SaintDanBert on 2009-10-19
> **awayguy said:**
> 
...
i've got on a 200gb harddisk two partitions. one: 135gb with vista. other one 48gb with ubuntu. and there is also this windows vista partition which is always there (to reinstall vista)
now let us think, i want to work a lot with ubuntu. would i be better to belay maybe 100gb with ubuntu and remove this "secure vista partition".
as I remember you can choose while installing ubuntu, how much space it should belay on the harddisk. and there i have also the posibility as a student, to install windows7 for free.
so now would it make sence to remove this "20gb emergency vista partition" or just let id because i dont need as much space and install on 80gb win7 and on 80gb ubuntu 9.10 ?


I recommend that you keep the vendor utilities partition on your drive.

Most laptops and many new desktop workstations have a vendor diagnostics and utilities partition. These are usually pretty small -- say 5-10GB. (I cannot speak for what Vista itself might do.) These utility partitions might have the "restore media" images and such. They also might have hardware diagnostics, special support software, and other similar goodies. In addition to magic contents, these partitions often require specific locations (as in primary partion #2, or primary partition #4) and specific attributes (who could guess).

Another potential use is for failsafe-backup space when the vendor provided tools run from the win-dose user interface. (They don't save your data, only certain of the system settings.)

Cheers,
~~~ 0;-Dan

---

### Post by awayguy on 2009-10-19
> **bulldog said:**
> I should decrease Vista as small as you can get **using the disk management utility build within Vista** so you will be sure your Vista will not be damaged by this action.
Defrag one or two times before you do so.

Next step.
Let's assume Vista will be decreased till say 100GB.
let the recovery partition as it is,
Now you'll have about 80GB space.

Create in this free space an extended partition about 12GB
Make a logical partition in the extended partition 10GB for /  [system]
Make a logical partition in the extended partition from the rest of the space 1-2GB for swap
Create a primary partition from the rest of your space 68GB give or take a few MB's, for a /home partition.

If you understand what I'm talking about we can go with a possible install
and the mount points.
If not,just ask your questions.


yep i think i got that right. i did this allready once on my pc and once on my notebook, so i know what you are talking about. i think i can do it, when not i will surelly ask.

so now, do you think i should have a try with win7 ?

---

### Post by bulldog on 2009-10-19
Win7 is the better choice in relation with Vista
I have Vista on a laptop but I set ubuntu next to it,and guess what I use the most.
I have worked a few months with win7 and it's a good OS.
But I'm in favor of Linux,so I did go back to ubuntu,but win7 is still installed on my hdd and so is XP.
But I rarely use them :)

---

