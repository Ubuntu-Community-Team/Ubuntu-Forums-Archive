---
title: "Unable to boot into Ubuntu"
date: 2009-08-12
forum: Installation &amp; Upgrades
---

### Post by Mach1723 on 2009-08-12
I installed ubuntu 9.04 using wubi on a external hard drive and the drive doesnt get loaded by the computer until after windows is started, so i have an ubuntu boot option but it gives an error since the drive isnt loaded.

---

### Post by sailthesea on 2009-08-12
I'm pretty sure Wubi won't work like that It virtualises the ubuntu OS within the windows disk It would work better to just install ubuntu fully on 2nd HDD and set grub to give you a dual boot
 Welcome to the forums and Ubuntu:P

---

### Post by Mach1723 on 2009-08-12
> **sailthesea said:**
> I'm pretty sure Wubi won't work like that It virtualises the ubuntu OS within the windows disk It would work better to just install ubuntu fully on 2nd HDD and set grub to give you a dual boot
 Welcome to the forums and Ubuntu:P
The Hard Drive doesnt appear in the, default boot drive manager(place where you choose boot from CD), so i need to know how(if possible) to get it too appear there first.

---

### Post by sailthesea on 2009-08-12
You would need to alter the BIOS setting of the machine to look for the second HDD as a boot option then you should have the option to boot into either system but you will have to use the ubuntu grub to do this as win bootloader will not recognise ubuntu as an OS 
 Also what do you see on the second HD if you explore it from Windows? Are you sure Ubuntu is installed as a OS there? I never tried that with Wubi. In theory it should work but it will be written as ntfs  which won't work as ext3 is the system used by ubuntu Wubi is really useful but no substitute for a hard install!

---

### Post by Mach1723 on 2009-08-12
> **sailthesea said:**
> You would need to alter the BIOS setting of the machine to look for the second HDD as a boot option then you should have the option to boot into either system but you will have to use the ubuntu grub to do this as win bootloader will not recognise ubuntu as an OS 
 Also what do you see on the second HD if you explore it from Windows? Are you sure Ubuntu is installed as a OS there? I never tried that with Wubi. In theory it should work but it will be written as ntfs  which won't work as ext3 is the system used by ubuntu Wubi is really useful but no substitute for a hard install!
It has the wubi folders(used wubi and normal install before).

---

### Post by sailthesea on 2009-08-12
OK back to the beginning 
 To get ubuntu up and running you have 3 options 
1 Install within Windows (on the same HDD as win) using Wubi
2 Create an LiveCD and use it to try a live session on your machine 
3 Use the Live CD to install Ubuntu on you 2nd HDD and dual boot your system
 I am assuming you don't want to get of windows yet But just want to try ubuntu and learn

---

### Post by Mach1723 on 2009-08-13
> **sailthesea said:**
> OK back to the beginning 
 To get ubuntu up and running you have 3 options 
1 Install within Windows (on the same HDD as win) using Wubi
2 Create an LiveCD and use it to try a live session on your machine 
3 Use the Live CD to install Ubuntu on you 2nd HDD and dual boot your system
 I am assuming you don't want to get of windows yet But just want to try ubuntu and learn
 I have a live Cd, i have installed it 3 or 4 times before, just didnt work with the external hard drive, and i dont have space for it on my main hard drive.

---

### Post by sailthesea on 2009-08-13
Install Grub
Google it 
Have to goto bed now Sorry

---

