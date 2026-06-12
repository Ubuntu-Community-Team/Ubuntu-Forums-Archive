---
title: "Triple boot: Grub help, please?"
date: 2009-02-17
forum: Installation &amp; Upgrades
---

### Post by BEND IT 7 on 2009-02-17
Hi, everyone.

Remember how a long time ago I said I wanted to triple boot Ubuntu and Vista with XP added on.  Well, I think I'm installing XP today.

The only thing I am hazy on is what to do once I have XP and Vista both installed and bootable with the Windows bootloader.  I still want to be able to boot Ubuntu.  In fact, I still want that to be my primary OS.  Vista will be for most of my Windows use.  XP will be for older programs (especially games such as AOE2 and IGI2) with various compatibility issues in Vista.  Ubuntu will be for everything else (in other words, most things).

So, I was wondering what to do to restore Grub after making XP and Vista both bootable in the Windows bootloader, and how to keep all three OSes bootable.

I am using a laptop so I will have to boot off of a UNetbootin flash drive for the Ubuntu live CD, if that changes anything.  And, yes, I figured out perhaps the easiest method to install XP from a flash drive ([http://netbooks.modaco.com/content/msi/261632/installing-xp-via-a-usb-stick/](http://netbooks.modaco.com/content/msi/261632/installing-xp-via-a-usb-stick/)  if anyone was curious).

---

### Post by Pumalite on 2009-02-17
The best way is to install XP first; Vista second and Ubuntu; last.

---

### Post by easybake on 2009-02-18
I have a triple boot going right now. After a bunch of trial and error I found the best way is as follows.

Partition your drive into 3 sections (i did this with a ubuntu live disc)

Install xp onto the first partition.

Insert the ubuntu live cd, go into partition editor, right click on the xp partition, select "manage flags", uncheck "Boot", check "hidden". Right click on second partition, manage flags, check "boot"
(by doing this you avoid the xp and vista being grouped together in the windows bootloader)

Install vista like you normally would onto the second partition. 

Put the ubuntu live cd back in. Remove all the 'flags' from all the partitions. Install ubuntu onto the third partition.

Once finished boot into ubuntu. 

(grub will probably only notice the vista partition so you have to manually edit, as root, the /boot/grub/menu.lst file in order to add the xp partition. (just copy and paste the vista option but change the title and root location to match xp))

---

