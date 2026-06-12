---
title: "Grub does not load after I've started Vista again."
date: 2008-12-01
forum: General Help
---

### Post by BlasterXL on 2008-12-01
I hope someone could help me with my problem. I'm new to Linux, but I have Ubuntu also installed on my laptop and (I'm loving it!).
 
The problem is that the Grub load menu does not load after I've started Vista again:

I have 2 harddisks of 1 terabite each. I had vista already installed, after that I installed Ubuntu 8.10 on the other harddisk and used the EXT3 format. Everything was fine from here, I updated Ubuntu and I restarted a few times, everything was fine........ Until I started Vista once again! Ofcource Vista worked but now my boot options are gone. Like Vista took over the whole starting progress, I can't make a selection anymore where I can start Vista OR Ubuntu. 

I found some similar topics in this forum, I'm new in Linux, I could not get me an awnser. I don't even know where to start looking.

When I boot from the Cd-rom (Ubuntu 8.10) it only gives me an option to install Ubuntu. Or start Ubuntu from CD-rom.

I just want my boot-menu back, now I can't even start Ubuntu. When I start my PC, Vista just starts.... And I hate Vista. Ohhh man, spend many hours  searching, who can help me??? :)

*Sorry for my bad English, I'm Dutch.

---

### Post by caljohnsmith on 2008-12-01
OK, how about booting your Live CD, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo grub
grub> find /boot/grub/stage1
grub> find /grub/stage1
```
One of the above commands should return your main Ubuntu partition (or /boot partition if you have one) in the form of (hdX,Y) where X and Y are numbers, for example (hd0,4), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
Please post the output of all the above commands, and also the output of:
```
sudo fdisk -lu
```
Reboot, and let me know if you get the Grub menu again.

---

### Post by BlasterXL on 2008-12-08
Wow, never though answers would be that quick, even the same day, crazy!
Thanks for your help! I got the outputs pasted below:

grub> find /boot/grub/stage1
(hd1,0)

grub> find /grub/stage1
Error 15: File not found

grub> root (hd1,0)

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.

sudo fdisk -lu
Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x6325b1f2

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2   *        2048   209715199   104856576    7  HPFS/NTFS
/dev/sda3       209715200  1953521663   871903232    f  W95 Ext'd (LBA)
/dev/sda5       209717248  1953521663   871902208    7  HPFS/NTFS

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xd52e5cfc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1935302354   967651146   83  Linux
/dev/sdb2      1935302355  1953520064     9108855    5  Extended
/dev/sdb5      1935302418  1953520064     9108823+  82  Linux swap / Solaris

---

### Post by caljohnsmith on 2008-12-08
OK, so it looks like you now have Grub properly installed to your Ubuntu sdb drive. The next step would be to run:
```
sudo sfdisk -A1 /dev/sdb
```
That will mark your first partition on the sdb drive as bootable, because even though Grub doesn't care about whether the boot flag is set in order to boot a partition, there are some BIOSes that will refuse to boot a drive that doesn't have the boot flag set on one partition. After doing the above command, reboot, set your BIOS to boot the Ubuntu sdb drive, and you should get the Grub menu. Let me know if you get that far or if you run into problems.

---

### Post by BlasterXL on 2008-12-08
Wow you are quick, I press F5, and got myself an answer, many thanks.
I did what you say.

ubuntu@ubuntu:~$ **sudo sfdisk -A1 /dev/sdb**
Done

I Changed the bios, and let the Ubuntu drive start first. 
Now I got myself a bootmenu! I can start Ubuntu now, but cannot start Vista. But I can see both options!

I press this option from the grub-boot-menu: 
**Windows Vista/Longhorn (loader)**     
> I see these words flashing in a second: 
[I]Starting up: 
GRUB Loading stage2[/I]
Then it brings me back to the main option menu.

When I select the second option (yes this option is twice in the menu):
**Windows Vista/Longhorn (loader)**     
It gives me an error:
Error 12: Invalid device requested, *Press any key to continu...*

So I can't start Vista now, but I can start Ubuntu, and the bootmenu is back.
Actually, this situation is better then before :D But it would be nice to have the option back to let me start Vista again.

Thanks again.

---

### Post by caljohnsmith on 2008-12-08
OK, that's great news you can at least boot into Ubuntu. Go ahead and boot into Ubuntu again, open a terminal and do:
```
gksudo gedit /boot/grub/menu.lst
```
And replace your two Vista entries with the following single entry:
```
title Windows Vista
root       (hd1,1)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Reboot, try Vista from the Grub menu, and let me know exactly what happens. We can work from there. :)

---

### Post by BlasterXL on 2008-12-08
You are amazing, serious. It works!! I just deleted the double entry and replaced the good one, with your codes above. I also changed the words *Vista/Longhorn* in *Monkey OS* This is amazing man!! 

So I started Vista with no problems, and the GrubMenu does still load, so Vista could not mess it up again. Also Ubuntu starts great now.

You really made my day, I even leaned alot of this. I'm even typing with a smile now! I can't wait to explore Ubuntu more!
I tell my friends, everyone, yoourrrrr amazing!!!!!!! Thanks 1000 times, and even more.

Compiz everything works great again. My next mission is to install OpenOffice 3.0! And the new Ati 8.11 drivers. 
Thankz for everything.

---

### Post by caljohnsmith on 2008-12-08
I'm really glad to hear it worked OK. Cheers and have fun with Ubuntu. :)

---

