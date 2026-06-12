---
title: "dual-boot GRUB overwritten; cannot boot Windows"
date: 2009-04-25
forum: Installation &amp; Upgrades
---

### Post by corsinnema on 2009-04-25
Previously I had changed the order of my dual-boot GRUB menu so that XP would load by default.
When I upgraded Intrepid to Jaunty, this GRUB menu got replaced with a single-boot menu. The windows partitions still exist and can even be mounted.
Is it possible to restore dual-boot by adding some lines to the new GRUB menu? If so, what do I put? 

Any help would be greatly appreciated!

---

### Post by Bauldronius on 2009-04-25
I am a noob in ubuntu but i think this will help
open terminal and type sudo gedit /boot/grub/menu.lst
there you will see a example looking like this
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
copy it to the end of the document "without #" where there is the boot menu list 
next you will need to find out what to type here: root        (hd0,0) so open a new terminal and type sudo fdisk -l and you will get a list looking like this:    
Device  Boot      Start         End      Blocks   Id  System
/dev/sda1               1        3647    29294496    5  Extended
/dev/sda2   *        3648       19458   126994432    7  HPFS/NTFS
/dev/sda5               1         486     3903732   82  Linux swap / Solaris
/dev/sda6             487        3647    25390701   83  Linux
for example this is my windows partition:
/dev/sda2   *        3648       19458   126994432    7  HPFS/NTFS 
sda2 means (hd0,1) sda1 means (0,0) etc
so what you should end up should look like this in the grub menu file
title        Windows 95/98/NT/2000
root        (hd0,1)
makeactive
chainloader    +1

---

### Post by zeex on 2009-04-25
> **corsinnema said:**
> Previously I had changed the order of my dual-boot GRUB menu so that XP would load by default.
When I upgraded Intrepid to Jaunty, this GRUB menu got replaced with a single-boot menu. The windows partitions still exist and can even be mounted.
Is it possible to restore dual-boot by adding some lines to the new GRUB menu? If so, what do I put? 

Any help would be greatly appreciated!

updating menu.lst will work but if you want another approach.

Boot with winXP CD -> go to repair mode -> at the command prompt type fixmbr. (This will update the MBR basically now you can boot XP but not linux). This step is equivalent to [removing linux]("http://stringofthoughts.wordpress.com/2009/03/29/removing-linux/") from the system.

Now boot with ubuntu live CD and [reinstall the grub]("http://stringofthoughts.wordpress.com/2009/03/29/re-installing-grub/").

See windows thinks it's the only OS in the world and that's why it removes the linux but linux has a huge heart. It plays along with every other OS :)

Good Luck :)

---

### Post by Luke771 on 2009-04-25
Dont do that!
Using the Windows CD to  repair the MBR will ... well, overwrite the MBR.
Your PC will boot straight into Windows and you'll have to use Windows own (sucky) boot loader to boot Linux.

Manually adding an entry to /boot/grub/menu.lst is the way to go.
Remember to edit menu.lst as root or you won't be able to save your changes
```
sudo gedit /boot/grub/menu.lst 
```

IF your Windows partition is on sda1 and your Linux partition is on sda2, add this entry: 
```

 title		Windows
 root		(hd0,0)
 makeactive
 chainloader	+1

```

To modify my example entry according to your own setup, answer the question: "on which partition is Windows?", then modify the 'root' line (second from top) according to this table:

Windows partition.... 'root' line.

___sda1  _______...____root (hd0,0)

___sda2  _______...____root (hd0,1)

___sdb1  _______...____root (hd1,0)

___sdc3  _______...____root (hd2,2)


It's about counting: physical discs first, partitions later.
The A in sda1 stands for first physical disc and the 1 stands for first partition (on that disk).
Therefore, the third partition on the second HDD would be sdb3.
The _first_ 0 in hd0,0 stands for first physical disc and the second zero stands for first partition. The third partition on the second HDD would be hd1,2 (the count starts from zero rather than 1).
In order to boot from sdb3 (third partition of the second HDD), your 'root' line should look like this:```

root    (hd1,2)
```

---

### Post by zeex on 2009-04-25
> **Luke771 said:**
> Dont do that!
Using the Windows CD to  repair the MBR will ... well, overwrite the MBR.
Your PC will boot straight into Windows and you'll have to use Windows own (sucky) boot loader to boot Linux.



Yeah That's why i told him to reinstall grub after fixmbr.

Although i'm curious how do you use *_windows bootloader_* to boot Linux

---

### Post by corsinnema on 2009-04-25
Thanks very much guys. You're full of beans! This improved my day quite a bit. Editing menu.lst worked wonderfully!

---

