---
title: "Installing to dualboot with Vista on new HP laptop"
date: 2009-02-18
forum: Installation &amp; Upgrades
---

### Post by Vektrat on 2009-02-18
Hello,

First of all I'd like to let you know that I hate asking and believe me it's my last resort (I've searched and checked, and couldn't find any clear help).


I just got a new laptop (HP dv5), which came with preinstalled vista and all the *awesome* bloatware.

I require to install Ubuntu so that I can boot either Vista or Ubuntu at my will, and I've done that in the past, however never on a new laptop with Vista.

I'd like to avoid doing a clean installation of Vista, I can't be arsed with the million drivers unless it's really necessary, specially since I got no disks (just a HD_RECOVERY partition with all of it - which could vanish when installing Ubuntu :p).


Anyway, I tried freeing space from the Windows Disk manager and it stays like that:
 (C:)
 (Unassigned free space - I chose 12Gb to install Ubuntu, only need it to program).
 HP_RECOVERY(D:)

After this I restarted with the Ubuntu CD inserted and booted it, the installation started normally, however when it comes to choosing the Partitions stuff, the fun starts.

I get this new graphic of Before/After:
BEFORE:  || /dev/sda1 93% (WinV) || Free Space 3% || /dev/sda2 2% (Recovery)

The options are the following:

·Guided - resize partition and use freed space: This is what makes most sense to use I guess, but I've read that this will screw my Windows Vista booting after the installation (Ubuntu will work though).
·Guided - use entire disk: No thanks
·Guided - use the largest continuous free space: This is the one I want to use having freed space previously from the Vista disk manager, HOWEVER when clicking here, the graph bar goes:
AFTER: || Ubuntu 8.10 100% || (Vista and Recovery seem to disappear).
·Manual: I want to avoid this, but it's no different from the rest.

I'd like to know if someone has/had experiences with HP laptops and their partitions :/

Thank you in advance :)

---

### Post by Eice on 2009-02-18
Hey,

I've installed Intrepid on my Vista Ultimate laptop (Compaq Presario CQ40, guess that counts as a HP machine) using the first guided option, with no visible ill effects.

---

### Post by Mark Phelps on 2009-02-18
If you've already freed up space using Vista's disk management routine, try downloading and burning a GParted LiveCD, and using that to format the free space as Ext3.  The Ubuntu partitioner should then see that partition and allow you to select it for use.

---

