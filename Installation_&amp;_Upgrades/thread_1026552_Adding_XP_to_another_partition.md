---
title: "Adding XP to another partition"
date: 2008-12-31
forum: Installation &amp; Upgrades
---

### Post by hoppyandy on 2008-12-31
Hi all, i have a fujitsu siemens laptop which came with vista pre installed but after many frustrations i look at linux and decided to put ubuntu on wanted to dual boot but through my mistake i managed to completely wipe the hard drive and finish up with ubuntu alone. Never mind hated it anyway.
i have tried to reinstall both vista and xp but neither will install. i partitioned the hard drive to give space but neither found it.
i am not desperate but would at some time like to add xp professional , i have it but when attempt to install it says there is no power to the hard drive, suspect i have either labelled partition incorrectly (dont know how to label or what to label it as) or a driver for the hard drive is needed ?
Have any of you guys any experience in doing this or had same problems.

---

### Post by taurus on 2008-12-31
How did you resize your harddrive, making room for windows?  Did you format that to fat32 or ntfs filesystem?  From Ubuntu, open a terminal and post the output of this command.

Applications -> Accessories -> Terminal
```
sudo fdisk -**l**
```
That is a lower case letter L, not number one.

---

### Post by hoppyandy on 2008-12-31
i didnt format it as anything i dont think. i used the ubuntu boot cd entered make no changes selection then used partition editor but i just slid the editor under resize / move.the space showed as unallocated space. i have since reallocated it all back to ubuntu so at the moment no extra partition, perhaps you could give a guide on how to do from scratch and how and what to label as, if you dont mind. maybe easier. Thanks

---

