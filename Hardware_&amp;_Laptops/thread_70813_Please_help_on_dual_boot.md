---
title: "Please help on dual boot"
date: 2005-10-01
forum: Hardware &amp; Laptops
---

### Post by dreaded 42 on 2005-10-01
Hello, I have problem being able to dual boot without changing bios. I have an asus a8v deluxe mobo. I have windows installed on a sata raid array. I installed 2 30g ide drives and used the software raid set up for ubuntu. I installed ubuntu no problem but can only boot to it if I change my boot sequence the bios. Then it will only boot to umbuntu and not xp. So i have to change bios back. when I hit esc at the ubuntu menu it does not see the windows installation on the array. I am completly new to linux. when I installed ubuntu it saw my array as separate drives with no partitions. I have also tried acronis boot os, it sees ubentu as an unknown os. when I try to boot to it, it just flashes a curser and does not load. I tried to load breezy thinking maybe a new driver is needed. But it only sees my array as 2 sepaerate drives. not the 2 30g drives. Any solution would be greatly appreciated. Remmember I am a complete noob to linux don't even how to run the command lines yet.

---

### Post by lisje on 2005-10-01
The problem is that Linux doesn't support your firmware/hostraid based sata controller. Hence Grub is not able to boot your Windows OS. It will only see the disks in your sata softraid array as individual disks. 
And there's nothing you can do about it to get it fixed, besides asking the manufacturer to publish the specifications about the controller and poke a kernel developper to submit a patch.

---

### Post by halfpower on 2005-10-02
If you press **F8** while booting an Asus A8V you will be brought to a boot menu.  From there you can choose which device you want to boot from.

---

### Post by dreaded 42 on 2005-10-04
Thanks for the info on the asus board works like a charm.

---

