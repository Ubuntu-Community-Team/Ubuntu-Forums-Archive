---
title: "after install ubuntu 7.04 , can't find dvd-ram drive in xp ???"
date: 2007-10-07
forum: Hardware &amp; Laptops
---

### Post by nigelc on 2007-10-07
hello everyone,
i'm using 
Lenovo 3000 N200
Intel Core 2 Duo 1.66GHz
512mb DDR2 X2
Hitachi Sata 120GB
HL-DT-ST DVDRAM GMA-4082N

follows are my harddisk partition
sda1 : 2x gb ntfs installed xp
sda5 : 6x gb ntfs for files storage
sda3 : 2x installed ubuntu 7.04

before install ubuntu, i can use my dvd-drive well. after installed, i can put ubuntu cd to boot up,
also i can find my drive in BIOS.
but somehow, after install ubuntu, and using grub to boot xp, i can't find my dvd drive in xp anymore.
even in ubuntu, i can see the cd-rom1, but when i try to open it, it say
 "special device/dev/hdb does not exist."

how can i find my dvd-ram drive in both os ??
thanks for your attention!

---

### Post by dinub1 on 2007-10-07
> **nigelc said:**
> hello everyone,
i'm using 
Lenovo 3000 N200
Intel Core 2 Duo 1.66GHz
512mb DDR2 X2
Hitachi Sata 120GB
HL-DT-ST DVDRAM GMA-4082N

follows are my harddisk partition
sda1 : 2x gb ntfs installed xp
sda5 : 6x gb ntfs for files storage
sda3 : 2x installed ubuntu 7.04

before install ubuntu, i can use my dvd-drive well. after installed, i can put ubuntu cd to boot up,
also i can find my drive in BIOS.
but somehow, after install ubuntu, and using grub to boot xp, i can't find my dvd drive in xp anymore.
even in ubuntu, i can see the cd-rom1, but when i try to open it, it say
 "special device/dev/hdb does not exist."

how can i find my dvd-ram drive in both os ??
thanks for your attention!

it needs to have a configuration for it in the file /etc/fstab

You need to go to system administartion, use administrator mode and enable that DVD-ROM. It is apparently disabled. I do not see the connection between Ubuntu and Windows XP. Those are independent O/S's and they run one not connected with the other. You may need to go to device manager in Windows XP Uninstall the VD-ROM driver and then let the Windows XP re-detect the device and install the corect driver for it. If it still does not work, then DVD-ROM may be defective.

---

### Post by nigelc on 2007-10-08
thanks for your reply,
but after i finished the installation, and login XP, i already can't find my dvd-rom in device manager.
i feel so weird. i use fixmbr to remove grub and start XP again. my dvd-rom come back......
so i wonder what's going on.

---

### Post by dinub1 on 2007-10-08
> **nigelc said:**
> thanks for your reply,
but after i finished the installation, and login XP, i already can't find my dvd-rom in device manager.
i feel so weird. i use fixmbr to remove grub and start XP again. my dvd-rom come back......
so i wonder what's going on.

So let me understand... With dual boot Windows XP and Ubuntu, DVD-ROM disappears from Windows? And after removing GRUB it disappears from Windows XP? Very strange...

When you look into device manager, do you see it there under CD/DCD devices? Do you get a yellow exclamation mark near it or it is not there at all?

---

### Post by dinub1 on 2007-10-08
How old is your Lenovo? Can you consider a sort of DVD-ROM malfunction? It may be defective.

---

### Post by nigelc on 2007-10-09
i bought it just two weeks ago.....
i  try to install 7.04 again, the same thing happened.
in device manager, no yellow exclamation mark.
the dvd-rom looks like disconnected with my notebook..... but the dvd power is on,and can be detected in bios. 
dual boot Windows XP and Ubuntu, DVD-ROM disappears in Windows, and after removing GRUB it appears in Windows XP.
so i fixmbr again, DVD-ROM appear again.
i think it is impossible that my DVD-ROM is defected.....
should i wait for Ubuntu 7.10 ?

---

### Post by dinub1 on 2007-10-09
> **nigelc said:**
> i bought it just two weeks ago.....
i  try to install 7.04 again, the same thing happened.
in device manager, no yellow exclamation mark.
the dvd-rom looks like disconnected with my notebook..... but the dvd power is on,and can be detected in bios. 
dual boot Windows XP and Ubuntu, DVD-ROM disappears in Windows, and after removing GRUB it appears in Windows XP.
so i fixmbr again, DVD-ROM appear again.
i think it is impossible that my DVD-ROM is defected.....
should i wait for Ubuntu 7.10 ?

Well power it may have. I also assume that when that happens you can open the tray of the DVD-ROM.
Hm... with Ubuntu installed, under Ubuntu does the OS see it? Say you insert a music CD into it, does it try to play?
This is very strange what is happening. I do not see any connection between the two OS's, they act and run independently. So I cannot see why will Ubuntu (and GRUB) installed, DVD-ROM device would disappear under Windows. Sorry that I cannot help.

---

### Post by nigelc on 2007-10-09
thanks for your help again.
i was confused too, i try Ubuntu 7.10 beta, it is the same.....
poor....
i'm going to try opensuse tomorrow, hope it can work well~
maybe i should send a email to Lenovo and ask for further information about that~

---

### Post by dinub1 on 2007-10-09
You are welcome. I am sorry that I couldn't help more. But that issue seems very strange, when you think that the 2 OS's are running independently. There is no link between the two. See what you can solve with Lenovo.

---

### Post by nigelc on 2007-10-11
i think it is the grub goes wrong....
i use lilo instead of grub, and it works!!~~

---

### Post by dinub1 on 2007-10-11
Sounds strange, but even if GRUB screws up sometimes, you can still make it find your boot partition and boot successfully. There is a procedure how.

Load and run a Live CD (Ubuntu, uses GRUB). Go to a terminal window.

type: grub

grub>  find /boot/grub/stage1

You will get a reponse like (hd0) where the boot partition is. in my case it is (hd0,2)

grub> root (hd0,2)

Make sure the number after hd0 matches your your boot partition found by GRUB

grub>  setup (hd0,2) 

Grub will repair itself for you and mark the boot partition

grub> quit 

Remove the Live CD and reboot from HDD. You should boot fine. it happened to me not once.

---

### Post by alvisetrevi on 2008-01-06
Hi, I had exactly the same problem. My "fix": install EasyBCd ([http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)) in Windows to rewrite the MBR and use the Windows bootloader instead of GRUB. You will still be able to boot into Ubuntu. This should make the CD drive appear again in Windows.
Still, this will almost surely not make it appear in Ubuntu!

Hope it helped,
Alvise

---

### Post by vonchiz on 2008-01-24
I had this same problem and couldn't get anyone to answer my posts.  It was a bear to fix, but here's how I did it.

From what I could tell, grub doesn't play nice with some removable laptop drives.  I tried several 3rd party boot loaders and either the problem replicated or Grub wouldn't boot linux.  

Step 1.  Replace Grub with Lilo as loutlined here
[http://users.bigpond.net.au/hermanzone/p4.html](http://users.bigpond.net.au/hermanzone/p4.html)
I used the apt-get option to install Lilo, the directions are good.
MAKE SURE you install Lilo on your Ubuntu partition and not on your MBR.

Step 2.  Install GAG as my bootloader.  Very straightforward.  Linux won't boot if you have your bootloader installed on your MBR.

If you know how to install grub on your linux partition and not MBR, it would work also.  I got sick of #($%ing around with it and switched to Lilo.

Hope this helps.

---

