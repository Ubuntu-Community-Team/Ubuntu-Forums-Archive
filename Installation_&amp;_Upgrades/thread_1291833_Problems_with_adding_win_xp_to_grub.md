---
title: "Problems with adding win xp to grub"
date: 2009-10-15
forum: Installation &amp; Upgrades
---

### Post by phrgarek on 2009-10-15
OK, first of all, i'm linux mint user(gnome)..... before i have ubuntu installed but i wanted to try mint.... 'cause mint is very similar to ubuntu i went to this forum 'cause on mint's nobody answers....
----------------------------------------------------------------------------
First i had only linux mint installed, than i shrinked linux partition with gparted livecd, to make a room for win xp.... i installed xp, lost grub, but i reinstalled grub with mint live cd and againg i have mint working, but win xp is not shown in grub menu, how to add win xp to grub menu.lst ?? please help
THNX

---

### Post by louieb on 2009-10-15
Your XP entry in /boot/grub/menu.lst will depend on where you installed XP.

1st or 2nd hard drive - which partition. 
a typical XP entry on the 1st or only hdd will look like 
```

title Win XP 
      rootnoverify (hd0,0)
      makeactive
      chainloader +1

```

If you need more help - then open a terminal window and post the output of 
```
sudo fdisk -l
``` lowercase L at the end 
Let us know how it worked out.

---

### Post by presence1960 on 2009-10-15
Let's get a better look at your setup & boot process. Boot into Mint. Come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

