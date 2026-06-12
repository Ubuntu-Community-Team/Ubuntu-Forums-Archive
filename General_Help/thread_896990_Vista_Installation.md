---
title: "Vista Installation"
date: 2008-08-21
forum: General Help
---

### Post by Ataris on 2008-08-21
Um...thank you, Microsoft, for writing an article against Linux. Your tutorial tells me how to install Vista by removing Linux. It even says that it assumes I want to remove it. Microsoft, you are truly helpful.

I have Ubuntu on my PC, and I don't want to remove it. I want to install Vista, and I suppose there is partitioning work involved. Does anyone have a guide on how to install Vista and not remove Linux?

---

### Post by Mhurst1 on 2008-08-21
You would need to install partiton magic install windows on the first partition and reinstall grub.

---

### Post by tuxulin on 2008-08-21
thats might be a little tuff
i think you need windows first the install bunty last

in your case if you install visty then it will wipe the bunty's
boot menu.

Tuxulin

edit 
Mhurst1 just might have the solution ticket :)

---

### Post by tuxxy on 2008-08-21
I would recommend installing ubuntu second but you can do what you want, try [this guide ]("http://knutee.net/?page_id=5")

---

### Post by WRDN on 2008-08-21
If you still have the Ubuntu LiveCD, boot from this, and open GParted (System > Administration > GParted). Now, resize the Ubuntu partition(s) and create a new **primary** partition to install Vista on. Note, this must be a primary partition, as Windows cannot be installed on Logical partitions. When Vista is installed, it will overwrite the MBR Ubuntu installed (GRUB), so you can rectify this by [reinstalling GRUB]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows").

---

