---
title: "linux mint gloriaRC1 problem"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by hit1808 on 2009-08-19
I was dual booting vista and mint gloria.
later i have **Installed** mint in my pendrive from the same System.The problem is everytime  i start, the grub is loading from ma pendrive
now evrytime i want to boot any O.S. ,i need ma pendrive inserted in order to load grub i hav given separete 15gb drive in ma harddisk for mint.
.is there anyway out i can load grub frm ma harddisk like i use to do it before?????.



*linux mint is ubuntu based so i thought its valid to post it on this site*

---

### Post by tgalati4 on 2009-08-19
Post the output of both /boot/grub/menu.lst, the one on the 2nd partition of your harddisk, and the USB one.

You might need use a chainload command or remap the drives.  When you include a USB drive, the drive order may change.

So as I understand it, you have Window/Mint7/removeable--USB-Mint7

---

### Post by hit1808 on 2009-08-20
i tried using sudo grub and setup(hd0)
but all i got was grub goin into infinite session durin boot
could you help me with those boot loader change commands

---

### Post by tgalati4 on 2009-08-20
Let's assume that your drives are set up as follows, with the pendrive plugged in:

/dev/sda1  Windows  GRUB calls this (hd0,0)
/dev/sdb1  Minty Goodness (15 GB drive)  GRUB calls this (hd1,0)
/dev/sdc1  Minty on Pendrive GRUB calls this (hd2,0)

sudo fdisk -l

This will list your drives, write them down for reference.  If different from above, note the differences.

cat /boot/grub/menu.lst

This will output your GRUB configuration when booting from the pen drive.


It would be helpful to cut and paste this to the thread so I can see what your current configuration looks like.

For windows you probably have something like:

title		Microsoft Windows XP Professional
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

You will basically comment out the linux lines and add

title		Minty Goodness (Linux Mint 7 Gloria based on Jaunty 9.04)
rootnoverify	(hd1,0)
savedefault
makeactive
chainloader	+1

title		Pendrive Mint
rootnoverify	(hd2,0)
savedefault
makeactive
chainloader	+1

Once you have that working from the pendrive try to boot into all three operating systems.  Then boot into Minty on the spare drive and make similar changes to it's /boot/grub/menu.lst.  Remove the pen drive and boot.  You should still see 3 choices, but the pen drive won't work because it's not plugged in.

---

