---
title: "Grub install problem solution on highpoint raid controller enabled motherboards"
date: 2008-10-20
forum: Hardware
---

### Post by renetwist on 2008-10-20
Hello Everyone,

I'm an owner of an Abit KT7A motherboard that has an Highpoint HPT370 Raid controller. It is an old motherboard but perfectly suited for some webserving and ftp serving.

Problem:
When I was installing Ubuntu (8.04.1 Server) the installation process worked like a charm. However, on the actual reboot no boot-loader was available. As I looked around I found out that during the installation process my regular controller was found as the second controller and my raidcontroller as the first. Grub however sees the regular controller as the first and thus the bootloader is installed in the wrong MBR.

Solution:

Step 1.
The solution is to insert your install cd again and choose "Rescue a broken system". When the system is done booting you will get a menu. From that menu choose to re-install grub. Choose the correct drive to write to and reboot.

Step 2.
On reboot you now will get the grub boot-loader. But there is still a problem. The devicemappings of grub are still wrong. To fix this select Ubuntu from the menu and press "e" to edit the lines of this menu choice. Edit the line that holds something like "(hdx,x)" where "x" is a number ofcourse. On my computer this should be "(hd0,0)". After altering that line pressing the "b" key will tell grub to load linux from the first disk and the first partition.

Step 3.
Wieeeh! Ubuntu loads! But once again another problem arises. Let's tackle that one too! The changes you make with the grub loader don't get saved. To fix this problem log in the system and open the "/boot/grub/menu.lst" file with an editor (you need full access to write to the file so be sure to type "sudo" when opening the file). Once the file is opened look for the same "(hdx,x)" as before. Change these values once more and close/save the file. Do an update of grub with the command "grub-install [device_path]" where "[device_path]" is the drive you need grub installed on. In my case it was "/dev/sda".

That's it, I hope this works as nicely for you as it did for me.

Cheers,

René Jansen

---

