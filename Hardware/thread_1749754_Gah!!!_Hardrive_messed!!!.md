---
title: "Gah!!! Hardrive messed!!!"
date: 2011-05-04
forum: Hardware
---

### Post by josh6190 on 2011-05-04
Hi all, in a serious pickle that escapes my knowledge. Heres a rundown. After the updates to 11.04 my computer after boot would freeze at the login woth no mpuse movement or keyboard response I later realized my netbook went into hibernation during the update proccess, thus corrupting the installation. I now have a totally wasted ubuntu partition. with a Windows 7 starter partition as well that thank god is still working so the entire machine isnt screwed. I'm planming on ridding the dell of its windows, and now the ubuntu will need rid of also. So, a total reformat of the hardrive, right? Not at all!! Disk utility and gparted running off a live ubuntu stick will not allow me to format the disk or do any think to it! I could read/write while everything worked, cept the ubuntu partition. So, I also have a grub menu. Which  initially after this mess is to have a small ubuntu partition for os, and a larger counterpart for data, no grub no windows. I'm unable to use my netbook, and need some serious help!

---

### Post by heyandy889 on 2011-05-04
Hey, dude. I like you signature, by the way. I don't really understand it, but it is still nice:popcorn:

So, the laptop won't boot. I applaud you for pulling out the old Live USB stick. That is exactly what I would have recommended. So, you're claiming that GParted won't let you modify the partitions. Hmm, that is interesting. Well, here's what I would say.

Boot into Ubuntu from the USB drive. Go ahead and open up GParted. Maybe post a screen shot or text from the error message that tells you that you're stuck.

In my experience, erasing partitions has been quick and easy. I would recommend trying to erase the Ubuntu partition, recreate it, format, and go on your merry way.

Good luck!

---

### Post by josh6190 on 2011-05-06
*Bump* guys i need some help

---

### Post by josh6190 on 2011-05-06
whoops osrry about the bump i dodnt see the replies

---

### Post by Grenage on 2011-05-06
I'll help if I can.

What error/message are you getting it gparted?  Do you *need* to clear the drive using gparted?  When booting from the Installation CD, you should have the option to overwrite the existing partition table (albeit, not in those words).

---

### Post by josh6190 on 2011-05-06
Anyway, I tried to open gparted via live and it wouldnt so i used disk utility, and sure enough i clicked format and mbr and it now claims i have 160gb free whoch was the size of the netbook hardrive.  so i believe thos thread is solved by accident! I just need to uninstall grub how do i do that?

---

### Post by Grenage on 2011-05-06
When you reinstall an OS on the drive, it will overwrite your existing grub entry - be that Windows or Linux.

---

