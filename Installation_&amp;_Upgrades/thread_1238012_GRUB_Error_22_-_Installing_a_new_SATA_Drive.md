---
title: "GRUB Error 22 - Installing a new SATA Drive?"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by XGhozt on 2009-08-12
Before I installed Ubuntu on my home box, (currently dual boting windows xp) I was able to just slap in new drives and boot the OS normally. I have to do this from now and then with other hard drives, to either retrieve data, format them or make backups.

I plug in the drive, and turn on the computer. The BIOS recognizes it because it prompts me to confirm the changes in hardware, and then I continue the boot process. As soon as GRUB starts to load, it fails with Error 22.

I searched for a bit, but I keep finding things about having to reload grub, but that doesn't make any sense. Shouldn't I be able to just swap drives around in my box without having any complications?

**So, my question is: How can I just temporarily install a new SATA drive and boot normally with just another drive in the system?**

---

### Post by madhavhmk on 2009-08-12
Does the list of operating systems appear during boot loading...?

or is it something like

boot loading...please wait
error 22

without the list of OSs?

---

### Post by madhavhmk on 2009-08-12
the problem might be because Grub is confused when it finds the partition with bootable OS is altered due to the extra HDD

you might need to reaarange your list of partitions, atleast, so that grub doesnt confuse the extra HDD with existing ones...

---

### Post by donpedrodos on 2009-08-12
The problem with the bootloader, in this case GRUB, it can get caught in a miscounting of drives.

As example, your boot HD was set in you menu.list to HD0,2.
Translated to normal Englisch: HD0 = first HD found by grub.
2 means the third (3) partition on the first HD.

So if you put in a new HD, GRUB can get confused about the order of finding you HD.
Probably Grub finds you HD the first in count, but there is nothing on it.

Some time ago i was strugling also with the same problems, the only thing you can do is make an edit at you bootscreen selection.
The moment that you selection for Ubuntu or XP pops up, you highlight you Ubuntu selection.
Then press 'e'(dit) and now you manual can change you HD number and partition number.
After you changed it, press 'b'(oot).
If it still fails, try another numbers.
If you have only 2 drives and 1 of then has 2 partitions, you can try the next settings:

HD0,0
HD0,1
HD1,0
HD1,1

And after finding the correct HD setting, edit you menu.list to reflect the correct settings for Grub.

If you want to learn more about GRUB, [go to the next page]("http://members.iinet.net.au/~herman546/p15.html") for detailed infromation

Goodluck

And this next part is for developers....

This issue is also menstioned in many forum questions, so it seems the time is right to finaly fix this kind of problems.
Grub should alway find the bootpartition, no matter how many drives i install.
It can use the Bios for a count of drives, but it needs to go a step further by checking every disk/partition for a kind of 'flag' that will tell him to boot that drive ( at least Ubuntu ).
And then let him skip the "HDx,x" info and startup anyway.
Next step is when Ubuntu is up and running ask people if they want to correct the menu.list AND if they want this drive to be 'automounted'.
These 2 files are important to the user to get everything back to normal, without being a computernerd.

---

