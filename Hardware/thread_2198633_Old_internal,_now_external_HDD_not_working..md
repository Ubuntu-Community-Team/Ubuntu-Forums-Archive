---
title: "Old internal, now external HDD not working."
date: 2014-01-09
forum: Hardware
---

### Post by adrian89 on 2014-01-09
So I have a 250Gb HDD which it was internally, but starting getting bad sectors on it so I changed it with a 500Gb one and the 250 I put it in rack(borrowed it from a friend), but I am experiencing some issues with it.
Ubuntu does not detect it properly,meaning, it appears in /dev but gnome disk manager and gparted does not detect it, tried to set the laptop to boot from the external one and it starts fined, but after I log in Ubuntu the screen remains black with only the mouse pointer showing and in Windows(cause I have dual-boot) it crashes right after the Windows logo appear.
I tried it on another laptop but gnome disk manager it shows that the disk has no partition and is empty and gparted loops in scanning devices.
Only windows 7 is capable of mounting succesfully the HDD, but I do not have acces to the ext4 partition from win7.
One more thing I tried, used a ubuntu 13.10 live usb which detected both HDDs but when I tried mounting the partition from the external HDD I get error, a huge long error, and gnome disk manager again shows the hdd empty and gparted stays a min on scanning and after that I start receiving errors that it cannot acces the external HDD's partitions.

My question is basically, could it be the rack to blame this? If I put the HDD back in the laptop as internal hdd, it works normally.

---

### Post by adrian89 on 2014-01-10
It was a rack issue, I've managed to get another rack for testing and it worked like it should.

---

