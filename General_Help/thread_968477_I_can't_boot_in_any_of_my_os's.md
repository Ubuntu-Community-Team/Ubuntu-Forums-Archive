---
title: "I can't boot in any of my os's"
date: 2008-11-02
forum: General Help
---

### Post by labou on 2008-11-02
I completely messed up my computer. I was trying to get a triple boot of vista, xp, and ubuntu, but i messed it up. I had it working well enough with the default ubuntu loader showing up first and then i could select vista\longhorn from there and boot from vista and xp. but i wasnt pleased with that and i wanted to have just one boot  menu. so i went into my vista boot cd and went into the command promt and did bootrec.exe /fixmbr and fixboot. after this i went back into vista and went into easybcd and add a neogrub menu for ubuntu. i thought this would work and it sort of did at first. it would load vistas boot menu; show me vista, xp and ubuntu and when i selected ubuntu it would load the default ubuntu menu and i could get into it like that. so with that i was ok. but then i tried to boot into vista and when it would get time for the vista welcome screen to show it would just stop. i wouldn't load the boot menu. so in my haste i made the bad choice of going back into my vista boot cd and do the same thing i did before (bootrec.exe /fixmbr). this ended up my ubuntu loader and it didn't even fix vista. now i cant load any of my os's...!!!??? can anyone help?

---

### Post by cmnorton on 2008-11-04
Here are some places to look:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
[http://ubuntu-rescue-remix.org/node/57](http://ubuntu-rescue-remix.org/node/57)
[http://ubuntuforums.org/showthread.php?t=967389&highlight=recover+boot+partition](http://ubuntuforums.org/showthread.php?t=967389&highlight=recover+boot+partition)

If you use Search/Advanced, and use "recover boot partition" as the search string, you'll see this problem has received a lot of attention.

---

### Post by caljohnsmith on 2008-11-04
How about booting your Live CD, open a terminal (applications > accessories > terminal), and posting:
```
sudo fdisk -lu
```
And please identify your partitions. Also, you could try doing the "Vista Repair" option from your Vista CD to hopefully at least get Vista booting again. Then it will be easier to sort out your boot problems.

---

