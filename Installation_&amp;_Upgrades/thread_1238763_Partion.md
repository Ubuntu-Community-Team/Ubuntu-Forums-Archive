---
title: "Partion"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by odiear3rd on 2009-08-12
I lost Wins XP Pro, it crashed. Installed Kubuntu 6.10 in its place. Now I want to Partion Them to c drive. Win Recovery cd says that wins cant see that the HD is installed. Does anyone have a solution to this problem?? I have pation kubuntu to 20gb and want 60 to wins.

---

### Post by oldfred on 2009-08-12
Windows partition editor will not see ext3 partitions. You need to use gparted. Your kubuntu 6.10 is pretty old so you should get a new copy of kubuntu and/or gparted. You have to run from a live CD to allow editing of the partitions.
You should not have to make the Windows partition first but be sure to make it a primary partition or else you will have issues with windows.

---

