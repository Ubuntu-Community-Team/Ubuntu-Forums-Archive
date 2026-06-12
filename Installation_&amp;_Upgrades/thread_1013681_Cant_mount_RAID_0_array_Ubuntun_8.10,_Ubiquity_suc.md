---
title: "Cant mount RAID 0 array Ubuntun 8.10, Ubiquity sucks"
date: 2008-12-17
forum: Installation &amp; Upgrades
---

### Post by TheMechanic on 2008-12-17
I cant believe I cant get this right. I have completely failed trying to install Ubuntu on a fakeraid array. Below is the info from dmraid and fdisk.


/dev/sdb: nvidia, "nvidia_aggiijdb", stripe, ok, 625142446 sectors, data@ 0
/dev/sda: nvidia, "nvidia_aggiijdb", stripe, ok, 625142446 sectors, data@ 0

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_aggiijdb1   *           1           5       40131   83  Linux
/dev/mapper/nvidia_aggiijdb2               6         255     2008125   82  Linux swap / Solaris
/dev/mapper/nvidia_aggiijdb3             256       12414    97667167+  83  Linux


Now, i have a boot partition as #1 (ext3), swap as 2, and root partition for 3. I can install and complete the installation without GRUB, but then im completely stuck, and it makes me extremely angry at myself. When i restart and try to chroot /target, the terminal tells me 

chroot: cannot run command `/bin/bash': No such file or directory

So i cant access anything else. If i install grub and dont restart, then i get access but cant mount the drive. My drive appears "media" but if i try to mount it says its busy. 

Someone please help, because i want to strangle the penguin right now >_< I have the alternate amd x64 cd and still get the same GUI thats on the desktop i386 disc. There is no option to choose the text-based installer.

So much for ubuntu being user friendly

---

### Post by joff13 on 2008-12-17
hi,

you need the alternate CD to install on a RAID 

[http://www.google.ch/search?q=ubuntu+raid+0+setup&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a](http://www.google.ch/search?q=ubuntu+raid+0+setup&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-GB:official&client=firefox-a)

[http://www.howtogeek.com/forum/topic/install-ubuntu-810-on-raid0-configured-laptop-with-vista-premium-installed/page/2](http://www.howtogeek.com/forum/topic/install-ubuntu-810-on-raid0-configured-laptop-with-vista-premium-installed/page/2)

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

have fun

---

### Post by TheMechanic on 2008-12-17
Ive already visited those webpages many times and still come up empty. I alreasdy downloaded the alternante amd64 installer from mirrors.kernel.org. MY question is, how can i access the text based installer? When i boot from cd, it just goes back into the regular installer.

Thanks!
Eddy

---

