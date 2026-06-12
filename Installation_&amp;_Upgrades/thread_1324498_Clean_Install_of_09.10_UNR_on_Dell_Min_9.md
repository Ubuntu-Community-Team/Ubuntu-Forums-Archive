---
title: "Clean Install of 09.10 UNR on Dell Min 9?"
date: 2009-11-12
forum: Installation &amp; Upgrades
---

### Post by pile_of_leaves on 2009-11-12
About a year ago, I bought a Dell Mini 9 and it came w/ the Dell version of 08.04 Hardy. I'm finally getting around to updating to 09.10 UNR. I've read some documentation, but still need some help. (I am new to Ubuntu, and 08.04 is my first experiment.) I understand 08.04 does not allow me to make a USB Stick (I tried sudo apt-get install usb-creator and the Terminal can't find USB Creator.) Well, I have Dell which runs Vista (for school) and plan on attempting a clean install of 09.10. 

Anyway, do I need to completely remove 08.04 from the Mini 9 in order to install 09.10? If so, how do I go about accomplishing this? Any other advice for a newbie would be appreciated! 

Thanks

---

### Post by darkod on 2009-11-12
First of all, if you are not aware, UNR has different look (menu wise) from standard desktop version. I would recommend running both as live CD (live USB) to check them out. Unless you already know that you like UNR 9.10.

For installing over 8.04 no problem. Do you need any data from it? Do you have it backed up somewhere?

If you don't need to worry about data, and you are happy with the size of your current partitions just do:
1. Boot from 9.10 USB created
2. Select manual partitioning when asked
3. Mount old / partition as / again, select ext4 for file system and tick format box
4. If you have separate /home you can mount it but not format it and it will keep your data. But in that case the filesystem on it would have to remain as it is. If you don't need any data from it just format it as ext4 too.

Enjoy your new Ubuntu. :)

---

### Post by pile_of_leaves on 2009-11-14
Thanks for your reply! I don't need any data the Mini 9's hard drive... So it sounds pretty easy! Thanks for the advice, too. I'll definitely check out both before I install one.

---

### Post by earthpigg on 2009-11-14
keep 9.04 UNR handy. on my dell mini 9, 9.10 fails to detect wireless.

the package that theoretically installs the drivers lets it detect the wireless card, but now it seems to get stuck at 'acquiring IP...'

---

