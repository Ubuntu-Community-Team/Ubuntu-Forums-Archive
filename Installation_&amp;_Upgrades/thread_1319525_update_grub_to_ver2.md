---
title: "update grub to ver2?"
date: 2009-11-08
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2009-11-08
I have old grub sitting in mbr and small dedicated partition. It does chainload all other systems incl xp, ubuntu and debian lenny, the linux have old grub in their root.

Now ubuntu 9.10 from today wants update the grub to grub2.

Q. what are the consequencies in such case? will I have now grub 2 in the ubuntu root or does it somehow install itself strigt to mbr or what do I have to expect with this update?

Can someone tell what was the result of the update?

---

### Post by dandnsmith on 2009-11-08
I suggest a search on grub2 - there have been several threads on just this topic recently. One user has had problems, and there are threads with useful refs for the changes in grub2.

---

### Post by drs305 on 2009-11-08
This link will give you an introduction to Grub 2 and links specifically to the upgrading from Grub section:
[https://help.ubuntu.com/community/Grub2#Upgrading to GRUB 2]("https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202")

There have been some problems with upgrades (Error 11). If you get that error message, there is a section on how to remedy it.


The good news is that upgrading to G2 initially presents the G2 menu via Chainloading from Grub, so you can test the G2 selections and make sure they work before committing to the full upgrade.

---

### Post by ottosykora on 2009-11-09
it looks quite dangerous operation!

I have the primary grub menu installed on separate grub partition and the primary grub in mbr. 
Will this be affected somehow or do I have to make some changes to it?
The main menu in such case is entirely done by hand, no automatic update works in such case. 

Is this case also considered by this update? I just wonder , since the update is in the normal security etc updates the updater in 9.10 suggests me since abt 2 days. 
It could happen that one day I will forget to remove the tick in front of it and the whole machine is gone then?

---

### Post by drs305 on 2009-11-09
> **ottosykora said:**
> it looks quite dangerous operation!

I have the primary grub menu installed on separate grub partition and the primary grub in mbr. 
Will this be affected somehow or do I have to make some changes to it?
The main menu in such case is entirely done by hand, no automatic update works in such case. 

Is this case also considered by this update? I just wonder , since the update is in the normal security etc updates the updater in 9.10 suggests me since abt 2 days. 
It could happen that one day I will forget to remove the tick in front of it and the whole machine is gone then?

I haven't upgraded a machine with a separate /boot partition. If the Chainload and Grub 2 menus work, then it should be safe to upgrade to G2. When you do this, a backup of your old menu.lst will be saved in the /boot/grub folder (You will be reminded of this during the upgrade).

As for your "manual" entries, you will have to recreate them in the new G2 format and place them in a custom file in /etc/grub.d/
During the upgrade, Grub 2 is going to look for installed systems on your machine and create a menu using the discovered OS/kernels. It may find the same OSs you have in your manual entry, but it won't directly import your own menu format.

---

