---
title: "sata controller &quot;gone&quot; after jaunty upgrade"
date: 2009-05-22
forum: Installation &amp; Upgrades
---

### Post by Pjukern on 2009-05-22
I have a Marvell MV88SX6081 8 port sata controller with 4x sata drives attached in raid5. (software raid)

I upgraded to jaunty, and now /dev/md03 is gone.

lspci -tv shows the card. But i dont remember how i installed it the first time, the guide i followed seem to be gone.

edit:
Seems like the controller and drives are there, its just the raid5 array thats gone..

---

### Post by Pjukern on 2009-05-23
a little update here.

It looks like mdadm.conf didnt have the raid5 array, only my other arrays.

with mdadm -A -s i somehow managed to create a new array called md_d2.

So after much fooling arounf i now have the array back, but with no filesystems..

Thanks ubuntu. Why would "do-release-upgrade" remove my array? This really made me loose my faith in linux as a stable OS. 

Luckily i had backups of most of my data.

---

