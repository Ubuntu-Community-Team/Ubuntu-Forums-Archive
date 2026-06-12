---
title: "Trying to replace Fedora 10/Windows XP with Ubuntu/XP"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by westea49 on 2009-01-03
I installed Ubuntu on a Gateway Laptop (M675)and was able to dual boot it with Windows XP.  With a few days of reading I was able to get the wireless interface to work with only a few setbacks.  I was so impressed that I wanted to dual boot my primary laptop (a Dell M6300). SInce I am new to "linux system admin" I let someone else setup the Dell for XP/Fedora10.  Unfortunately, the wireless never worked and my attempts probably messed up the wired connection.  I reinstalled Fedora 10 (but with the gnome instead of KDE) and got the wired connection to work BUT the software that I used to study the laptop network get the wireless to work on the Gateway are not the same in Fedora.  They look similar but the Network Manager/Tools are significantly different.  I was going to take the easy way out and simple replace Fedora with Ubuntu.  HERE IS THE PROBLEM:  When I bring up Ubuntu it shows the XP and Fedora partitions BUT it does not allow me to replace Fedora;  it seems to want to eliminate both partitions. The only option I see is back up Windows, reinstall Windows and then load in Ubuntu???:(

---

### Post by taurus on 2009-01-03
From the LiveCD, open a terminal, Applications -> Accessories -> Terminal, and post the output of this command.

```
sudo fdisk -l
```

---

### Post by ajgreeny on 2009-01-03
From the ubuntu live CD you can also run System > Administration > Partition Editor and see how the partitions are arranged.  You may also be able to delete the fedora partition from this and then use the space to install ubuntu.

Generally when I install a linux distro, now that I know what I am doing, I find it a lot easier to delete partitions I don't need and then make new ones before going to the install.  It is much less confusing, particularly if you have a windows install which is precious to you.

---

### Post by meindian523 on 2009-01-03
or you can do manual partitioning and carefully delete your Fedora partitions and then create partitions for Ubuntu.Be sure to confirm which /dev/sdx,y corresponds to which partition on your HDD.The task will be much easier if sizes of said partitions are different.

---

### Post by Pumalite on 2009-01-03
Best way is to go 'Manual' and install on top of Fedora. You can ignore /swap. You'll have a brand new Grub with Dualboot.

---

### Post by westea49 on 2009-01-03
THanks for all of your suggestions. I will probably make a backup of windows in case I trash it. Not a big loss since my laptop is "my work at home computer" and my desktop at work is suppose to have all of my files but??? THanks again.

---

### Post by westea49 on 2009-01-03
Thanks again for your help on partitioning the system to remove the Fedora 10.  I stumbled thru it a couple of time but it was worth it.  After loading Ubuntu, installing the updates, Ubuntu recognized my wireless hardware and my Nvdia video and I have a fully functioning system AND I did not destroy my Windows partition (yet).  I am ready for work.  Thanks,:D

---

### Post by meindian523 on 2009-01-04
cool.Please mark the thread solved.

---

