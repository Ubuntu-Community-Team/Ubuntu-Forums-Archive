---
title: "GRUB problems with Windows Boot Manager"
date: 2009-02-03
forum: Installation &amp; Upgrades
---

### Post by shanmugamt on 2009-02-03
Hi, I installed Ubuntu using Wubi and few days ago tried Lubi to move Ubuntu out of Windows. When i do that I got installed GRUB as well. Now my system has two boot managers from Ubuntu and Windows Vista.
GRUB comes on the screen first and then Windows Boot Manager(WBM) next.
It went well for a day and then I couldn't load neither GRUB nor Windows Boot Manager (WBM).
I could see a message on the top left corner "GRUB Loading <<some version number here>>...." and keep rebooting. Since I couldn't reach either GRUB or WBM, I couldn't start my system.

Tried to troubleshoot all possible and then finally decided to reinstall Vista from the scratch.

Last night I reinstalled Vista. My question is:
Can we have one single Boot Manager,either GRUB or Windows Boot Manager?
When we have both how to handle when the first boot manager is failed to let the user in?

Thanks,
Shan

---

### Post by kestrel1 on 2009-02-03
Yes, you just want to have Grub. After installing Vista, Install Ubuntu in its own partition & let it setup Grub for you.
Should work, with no problems.

---

### Post by caljohnsmith on 2009-02-03
> **shanmugamt said:**
> 
Last night I reinstalled Vista. My question is:
Can we have one single Boot Manager,either GRUB or Windows Boot Manager?
When we have both how to handle when the first boot manager is failed to let the user in?

Thanks,
Shan
Yes, you can use one single boot manager. If the first boot manager fails, you have to either fix it or use another boot manager. Do you have Ubuntu still installed to its own partition on that HDD, or did you erase that too? I would recommend sticking with Grub to boot both Ubuntu and Vista, but if you really want to use Vista's boot manager, I would recommend checking out [EasyBCD]("http://neosmart.net/dl.php?id=1").

---

### Post by shanmugamt on 2009-02-03
> **caljohnsmith said:**
> Yes, you can use one single boot manager. If the first boot manager fails, you have to either fix it or use another boot manager. [EasyBCD]("http://neosmart.net/dl.php?id=1").

Thanks for the quick reply. Could you please let me know how to fix when the first boot manager fails?
I still have Ubuntu installed on a separate partition. but GRUB has been overwritten by windows Boot manager.

---

### Post by caljohnsmith on 2009-02-03
> **shanmugamt said:**
> Thanks for the quick reply. Could you please let me know how to fix when the first boot manager fails?
I still have Ubuntu installed on a separate partition. but GRUB has been overwritten by windows Boot manager.
It depends on what you are using as your first boot manager; if you are using Grub, you can follow these directions:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

But if you are instead using Vista's boot manager, you would probably have to repair it from the Vista Install CD.

---

### Post by shanmugamt on 2009-02-03
> **caljohnsmith said:**
> if you are using Grub, you can follow these directions:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

Thanks much Caljohnsmith.
It's very useful info. I will bookmark it. Unfortunatly I dont have Ubuntu Live CD. So, I just reformatted my vista and may have to reinstall Ubunutu. 
I tried to cut the Live CD twice using the downloaded images from [http://releases.ubuntu.com/intrepid/](http://releases.ubuntu.com/intrepid/). But it didn't help. 

Do you think there could be some better place to download the CD image?

---

### Post by caljohnsmith on 2009-02-03
That link for the Ubuntu Live CD ISO images should be just fine. Are you sure you are burning those ISO files to your CD as "images" and not burning them as a data CD? Also, I would try burning at 4X speed to help ensure better burn quality.

---

### Post by shanmugamt on 2009-02-03
That's correct. I am burning as image. I am getting the starting screen and that's it. I will apply your suggestion this time and attempt one more time. 
Thanks again Caljohnsmith.

---

