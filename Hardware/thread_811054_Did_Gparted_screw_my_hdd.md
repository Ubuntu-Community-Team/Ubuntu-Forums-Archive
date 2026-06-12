---
title: "Did Gparted screw my hdd?"
date: 2008-05-28
forum: Hardware
---

### Post by The MAX on 2008-05-28
So I was having major issues with dual booting ubuntu on my 250GB seagate, see last couple of pages of this [Grub Error 17 thread]("http://ubuntuforums.org/showthread.php?t=442945&highlight=Grub+error+17").
So used gparted to shrink my 200GB xp install to 60B then installed a 40gb ubuntu partition. Should have another 130GB (roughly) to do more stuff with....wrong.
Restarted and all the grub errors were gone and everything worked fine except when I went back into gparted to create a new ntfs for a second windows partition it only recognized my drive as being 130GB total....not cool.
Rebooted and the bios only detects 130 as well.
Wiped all partitions and no change.
I'm pretty peaved about this. have been trying to get this dual boot up and running for over a week now, and now my hard drive is supposedly 100 gb less then what it was an hour ago.

Help my obi-unbuntu forums-kenobi, you're my only hope.

---

### Post by Wej on 2008-05-28
How old is your motherboard? Older boards only had the ability to use 128GB of a hard drive, no matter how large it was. They went to 48 bit addressing on newer firmwares and boards. You can check to see if you have the latest BIOS for your system.

Also check on the hard drive itself to see if there is a jumper to put it in compatibility mode, which will limit it to display as a 128GB drive.

---

### Post by The MAX on 2008-05-28
mobo is 2005. had the system for almost 3 years and have had a 250, ran gparted and all of a sudden its 136... didn't change jumpers, didn't change mobo or bios. Only thing that changed was I ran gparted.

---

