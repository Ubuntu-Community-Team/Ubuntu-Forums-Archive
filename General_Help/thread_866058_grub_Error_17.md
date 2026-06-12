---
title: "grub Error 17"
date: 2008-07-21
forum: General Help
---

### Post by studunn on 2008-07-21
So i got a new wireless device a Alfa 500mx usb wireless adapter. i had some trouble configuring it in Linux so decided to dual boot vista and see how it worked. repartition the hard drive with gparted and everything worked great. i installed easy bcd as a boot loader. **now the problem** when i try to boot into ubuntu i receive an error 17...file not found. what can be done about this? has my ubuntu partition been fried? if so how and why? if the situation is irreconcilable, ie i am going to have to reinstall ubuntu, can someone give me direction so this doesn't happen again. i became a full time ubuntu user because my windows partition got fried. i dont want to have to go back..

---

### Post by dracayr on 2008-07-21
do you external hdds/flash drives etc or a new hdd connected that wasn't connected before? If so, try disconnecting it.

Else, while in the boot menu, hit 'c'. A grub prompt(grub>) should appear. execute

find /boot/grub/stage1
find /grub/stage1

Does that give any output?

dracayr

---

### Post by studunn on 2008-07-21
for the first input find /boot/grub/stage1, the output is: (hd0,1)

for the second input find /grub/stage1, the output is: 
error 17: file not found


there are no external devices connected, nor were there any when the system was set up.

---

### Post by BwackNinja on 2008-07-21
Since grub is even giving you that message, I'd say that an entry must be wrong due to repartitioning. Is the first line in the entry for ubuntu in the boot menu (press 'e' to see this) "root (hd0,1)"?

---

### Post by studunn on 2008-07-21
no, the drive listed was (hd0,0) I changed it to (hd0,1)and am now able to boot into ubuntu.

---

### Post by studunn on 2008-07-21
i spoke too soon. i am able to change it to the correct drive directory when i boot up, but it is not permanent. how do i make the change permanent?

---

### Post by Tim Sharitt on 2008-07-21
To make the change permanent, you will have to change the drive in the menu.lst file
```
sudo nano /boot/grub/menu.lst
```
Just change the same line you changed at boot time.

---

### Post by studunn on 2008-07-21
ok that worked, but after i select neo grub to load i still have 3 different boot options. i am using easyBCD as a boot device is there anyway to have it automatically boot a specific option?

---

