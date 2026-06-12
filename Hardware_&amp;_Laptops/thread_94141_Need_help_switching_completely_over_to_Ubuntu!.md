---
title: "Need help switching completely over to Ubuntu!"
date: 2005-11-23
forum: Hardware &amp; Laptops
---

### Post by aznboi on 2005-11-23
ok so when i first installed ubuntu, i isntalled xp then had ubuntu resize the hd to make half xp half ubuntu. I never use my xp side so i want to delete it and add the existing space onto my ubuntu drive.... how do i do this? thnx

---

### Post by earobinson on 2005-11-23
you could use gparted and just deleate the windows partition, then make the ubuntu one bigger, You will also have to edit /boot/grub.list (not on my ubuntu box but its the grub file in /boot) to take the windows boot option out.

---

### Post by aznboi on 2005-11-23
thnx! ok so im doing apt-get install gparted right now and ill see if i can figure it out.... if anyone knows how to edit the grub.list file plz tell me becuz i dont lol.. plus i dont see the grub.lst file lol....

---

### Post by aznboi on 2005-11-23
ok i think i kno which one to delete but which one is it just to make sure i dont delete ubuntu by accident lol...

still need help editing grub file....thnx

---

### Post by aznboi on 2005-11-23
ok just finished wiping it.... now how do i combine the two? thnx

---

### Post by aznboi on 2005-11-23
ok so i have successfully removed the windows option from the grub menu. Now all i need is instructions on how to merge the two partitions. thnx

---

### Post by SickTwist on 2005-11-23
First of all, playing with partitions is always a little risky so it is a good idea to make sure that you back up anything important before you proceed.

One of the [limitations]("http://www.gnu.org/software/parted/parted.html#features") of resizing ext3 is that the beginning of the partition must stay in the same spot. (All you can do is move the end of the partition). From the looks of your screenshot you have a few options:

1. Instead of changing the partition layout, you could just format hda1 as ext3 and mount it somewhere. (perhaps /home or /mnt/mystuff).

2. You could resize hda1 to about 6 GB and reinstall Ubuntu there. It may be possible to just copy the data from hda2 to hda1 to avoid the install procedure. Doing so would require you to edit a few files (/etc/fstab and /boot/grub/menu.lst) and then grub-install would need to be run. Once Ubuntu is on the new 6 GB hda1 (and you have tested it to make sure that it boots) you could delete hda2 then create a new hda2 partition using all of the available space. Then you could mount hda2 wherever you want (/mnt/mystuff, /home, wherever).

3. Wipe the HDD clean and start over with one large partition for Ubuntu. This is probably least optimal. Besides, I think that it is better to have a separate partition for /home anyway but it is your choice.

Let us know what you want to do and we can give you more detailed instructions if you need them.

---

### Post by aznboi on 2005-11-24
yea i would reinstall ubuntu completely becuz i could reconfigure everything easily, but i dont have the CD for it, and i dont want to wait to download it lol... So i think ill just make a new partition and mount it. Thnx.

---

