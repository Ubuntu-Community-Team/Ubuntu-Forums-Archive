---
title: "uninstallation problem"
date: 2009-02-26
forum: Installation &amp; Upgrades
---

### Post by bharath.ase on 2009-02-26
I am a newbie to this forum.

I want to uninstall ubuntu and install it again in a different partition.

I tried deleting the partition
but i could not boot vista

error message was Grub could not load bootmgr

can someone help me in uninstalling ubuntu properly without any damage to vista or xp.

Thanks in advance.

---

### Post by cariboo on 2009-02-26
When you removed Ubuntu, you removed grub, so you will have to use your Vista boot disk to restore the master boot record. Insert your Vista boot disk and boot from it and choose repair from the menu.

Jim

---

### Post by Herman on 2009-02-26
Just install Ubuntu again and then after that you'll be able to boot Vista again.

Neither Ubuntu nor GRUB will damage your Vista partition, it's only that the hard disk's MBR has been changed and that's not part of Vista. The MBR was changed to point to GRUB in Ubuntu but you have deleted Ubuntu and GRUB with it. When you re-install Ubuntu, that will fix it automatically.

You can do what cariboo907 said and change the MBR to point to your Windows boot sector again if you want to, but if you're planning on re-installing Ubuntu right away, you will have wasted some of your time and energy as re-installing Ubuntu will automatically re-install GRUB and that will fix it anyway.

The easiest and quickest thing to do would be to just re-install Ubuntu.

If it makes you feel better, here's a whole page full of ways to uninstall Ubuntu and make your Windows boot again by itself,  [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

Regards, Herman :p

---

### Post by bharath.ase on 2009-03-01
Thanks a lot for the help. Now one more question? If i just want to uninstall ubuntu only how should i do it. Can someone give me command line methods.

---

### Post by Herman on 2009-03-02
Here's a whole page full of ways to uninstall Ubuntu,  [Un-install Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm"), please let me know let me know what part of it you have difficulty understanding and I will try to give you more help. 
I will also edit the page to make it easier for others is the future. 
Regards, Herman :)

---

