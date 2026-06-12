---
title: "Partition will not go away"
date: 2007-08-25
forum: Hardware &amp; Laptops
---

### Post by BillGod on 2007-08-25
i have a 320gb  drive.  I have 2 partitions on it. sda1 is 280gb and sda2 is 30gb.  I am not sure how to explain what is going on.  when you copy something to the drive it takes easily 10 times longer than it should... YES THE DRIVE IS FINE!  I think its the file system.  If I try to mount the drive i get mount: special device /dev/sda1 does not exist  yet if I fdisk or check with gparted its there.  gparted shows a yellow ! when I check the info on the drive it says open /dev/sda1:no such file or directory	.  If I make any changes to the partition say delete both of them.. reboot then create new ones sda1 200gb and sda2 100 gb gparted fails and it remounts the 280gb partition.  I have even deleted the partitions and formated them as fat32 then tried to change them to new partitions and the original 280 and 30gb partitions keep coming back.  Does anyone have any ideas on what to do?  I am confident that if I take the drive out and put it in my windows box and repart and format the drive there.. then put it back in my linux box I will be ok..  Im just feeling lazy and dont want to do that.. besides gparted should work.

---

### Post by merlinus on 2007-08-25
You might try gparted live cd:

[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

unless that is what you are already using....

-merlin

---

