---
title: "Weird Issue"
date: 2009-05-28
forum: Installation &amp; Upgrades
---

### Post by rickyroger0907 on 2009-05-28
Hi, I've got this very strange problem going. Here goes, I just got a brand new desktop. After I installed Vista on it, I installed Ubuntu amd64. (my drive is 500GB, 65GB for WINDOWS, 300GB for stuffs in Windows-NTFS; I installed Ubuntu on a different 50GB partition, then another 50GB for Home Folder, 8GB for swap area). Then everything works fine, I can choose between the two at start-up. A couple days later, I have some problems with Vista. So I reinstalled Vista (I think this is where the problem came into live). After that, I can't choose between the two OS anymore. I even tried to reinstalled Ubuntu, but still I can't find it anywhere. Hope you guys can help me out here. Thanks for any reply. Appreciate.

---

### Post by tommcd on 2009-05-29
Reinstalling Vista will overwrite the MBR. So grub was erased from the MBR. That is why you can no longer choose to boot Ubuntu.
If you did a complete reinstall of Ubuntu though, that should have reinstalled grub to the MBR.
When you reinstalled Ubuntu (after reinstalling Vista) did the reinstall complete successfully? If so, then you can try reinstalling grub to the MBR. Follow this guide:
[http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck](http://ubuntuforums.org/showthread.php?t=224351&highlight=fsck)

---

### Post by rickyroger0907 on 2009-05-29
The first trial I encountered some weird problems, as it stopped at 90% (saying checking hardware), so I had to try another time, and it was a success. Still can't choose to boot Ubuntu. Thanks for your help. I'll try the other option.

---

### Post by rickyroger0907 on 2009-05-29
Thanks tommcd, it works. really appreciate it.

---

