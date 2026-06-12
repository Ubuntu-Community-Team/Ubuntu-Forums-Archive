---
title: "[SOLVED] Help me get back windows"
date: 2008-09-30
forum: General Help
---

### Post by FrequencyHopping on 2008-09-30
Plz help an absolute beginner.

I want to add windows xp to my system so I can dual boot, I've already had ubuntu on my system for a long time and want to keep the files I have on there. If I added ubuntu second it be so easy with the guided partitioning upon setup, but I want to do it the other way around. I've already used gparted to shrink the primary partition so I've got free space.

---

### Post by WWSmith36 on 2008-09-30
You can install windows on a new primary partition.  The only problem you will have is that windows will overwrite grub.  When this happens you will not be able to boot to ubuntu.  You will have to reinstall grub from the live CD and then edit you /boot/grub/menu.lst to include your windows entry

Here are some instructions (follow quick start 1-6) 

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Hope this helps

---

### Post by phidia on 2008-09-30
Windows will set up the MBR (master boot record) for itself only but you should only have to re-install grub to get a dual boot.

Look at the **Other installation guides** [here]("https://help.ubuntu.com/community/Installation") from the Ubuntu wiki.

---

### Post by FrequencyHopping on 2008-09-30
Thanks for the quick reply, I followed the instructions in the link and  it worked. Strangely I've now got some autocheck error message when booting into windows but I'll get that resolved some other time.

---

