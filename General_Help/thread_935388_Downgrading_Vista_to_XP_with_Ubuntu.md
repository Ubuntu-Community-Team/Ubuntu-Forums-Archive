---
title: "Downgrading Vista to XP with Ubuntu"
date: 2008-10-01
forum: General Help
---

### Post by food789 on 2008-10-01
I have a dual boot between Vista and Ubuntu, and I want to downgrade Vista to play my games faster.

So I'm wondering if I downgrade will I be able to update my GRUB with "sudo update-grub"? Would it work fine?

---

### Post by Elfy on 2008-10-01
#you'll need to reinstall grub, you cna use the buntu livecd to do so. You don't need to update-grub

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by bodhi.zazen on 2008-10-01
You will need to re-install XP and I presume the windows installer will over write grub (as it typically will).

You then simply restore grub :

[uwiki]RecoveringUbuntuAfterInstallingWindows[/uwiki]

---

