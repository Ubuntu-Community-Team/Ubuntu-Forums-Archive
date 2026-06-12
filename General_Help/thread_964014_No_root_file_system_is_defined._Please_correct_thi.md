---
title: "No root file system is defined. Please correct this from the partitioning menu error"
date: 2008-10-30
forum: General Help
---

### Post by labou on 2008-10-30
I downloaded the the latest version of ubuntu ultimate (1.9) the other day and tried to install it. After I burned the iso it brought up the wubi installation which gave me the choice to install ubuntu inside windows(vista in my case), so i did. I installed it in my main drive C: since it had enough space (around 50 gigs). Everything went smoothly through the install, but when i restarted and selected ubuntu from the boot up menu i got an error saying, "No root file system is defined. Please correct this from the partitioning menu." I don't understand why this happened or how to fix it. Can anyone help me out? (by the way, i also have xp installed along side ubuntu)

---

### Post by labou on 2008-10-30
bump

---

### Post by andrewabc on 2008-11-01
I have a similar problem. The same error message when I try go to the next step when installing.
The livecd i386 installer is not recognizing my hard drive or any partitions. The partitions section (part 4 of 7) is blank.
I am not trying the ubi installer.

The RC worked fine for me to install (and alpha6 and beta recognized my partitions). Luckily I still have the RC iso, so I guess I will have to install the RC.


@labou
If you have decent bandwidth I would suggest trying the Release candidate and see if it recognizes your partitions.

EDIT:
Ignore what I said about getting the RC
I restarted computer with livecd, but this time I did not  mount my two windows partitions, and the partition editor worked fine.
So it seems that partition editor might not work if partitions are mounted.

---

