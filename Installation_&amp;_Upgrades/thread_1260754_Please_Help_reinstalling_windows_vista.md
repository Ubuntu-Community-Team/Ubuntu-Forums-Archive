---
title: "Please Help reinstalling windows vista"
date: 2009-09-07
forum: Installation &amp; Upgrades
---

### Post by ananbehh on 2009-09-07
[COLOR=black][FONT=Verdana]Hello,[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]I have a Acer 6530G 64Bit laptop, I installed ubuntu, as the only operating system, on it and now I want to uninstall ubuntu and install vista again, so I got my recovery disks and started installing windows vista everything went fine during the installation, but after the installation completed system restarted and start booting, and after the bios menu I got error "Grub Error 17", I tried more than once and got the same error. [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Windows can’t load for some reasone.[/FONT][/COLOR]
 
[COLOR=black][FONT=Verdana]Any IDEAS...?:confused:[/FONT][/COLOR]
 
 
[COLOR=black][FONT=Verdana]Thanks in Advance.[/FONT][/COLOR]

---

### Post by running_rabbit07 on 2009-09-07
Using the LiveCD open gparted and delete the partition table and then create an NTFS partition across the whole disk.

Then install Vista.

---

### Post by ananbehh on 2009-09-07
Can You tell me how  to do this...Please

---

### Post by MC707 on 2009-09-07
ditto running rabbit.

any reason you wanna go back to the dark tunnel? I also installed ubuntu in my acer lappy and am overall happy. a damn annoying crap here and there but it works in the most part.

---

### Post by ananbehh on 2009-09-07
The reasone:
 
I cant get drivers to work on ubuntu Sound card, wireless card...etc.

---

### Post by MC707 on 2009-09-07
> **ananbehh said:**
> Can You tell me how  to do this...Please

[s]insert the ubuntu live cd. continue installation as if you were gonna install ubuntu again. when you reach the partition editing, choose 'manual' option. then, select the partition and **erase it.** then click on the 'free space' (that will appear after you delete the partition) and select on the option to create partition. Select nfts for the filesystem and apply changes for partitions. then exit the installation and install vista on the newly created partition. hope that helps[/s]

---

### Post by MC707 on 2009-09-07
> **ananbehh said:**
> The reasone:
 
I cant get drivers to work on ubuntu Sound card, wireless card...etc.

have you tried choosing **'hardware drivers'** under the system menu? installing proprietary drivers usually solves all problems. even my ATI and broadcom drivers work out of the box in my lappy.

---

### Post by Cheezespread on 2009-09-07
> **ananbehh said:**
> Can You tell me how  to do this...Please

Presuming you have the Linux live cd with you.
1.Boot up your Ubuntu install CD (select the Try without installing option at the CD boot menu) 
2.go to System>Administration>Partition Editor ( I guess thats where it is ). This will run gparted.
3. You can create an NTFS partition out of the whole disc space as rabbit mentioned.
4.After that , reboot and Install Windows Vista.

---

### Post by MC707 on 2009-09-07
> **Cheezespread said:**
> Presuming you have the Linux live cd with you.
1.Boot up your Ubuntu install CD (select the Try without installing option at the CD boot menu) 
2.go to System>Administration>Partition Editor ( I guess thats where it is ). This will run gparted.
3. You can create an NTFS partition out of the whole disc space as rabbit mentioned.
4.After that , reboot and Install Windows Vista.

oh yeah I think that works better, my bad.:oops:

---

### Post by kennethadammiller on 2009-09-07
I don't remember that the live cd offers an option to edit things to  other partition types ect, only the install preferences. Gparted live will though, and it's very easy to use. just boot from it like you did the live cd. Just google gparted live it will take you where you need to go. burn the iso, boot up, and you will come to a screen that offers many different options (this being the gparted disc that i use which i haven't updated) and then after that just press enter. select the appropriate language and keyboard and then go from there it's very quick. It will show a table of partition types. whatever they are, just delete them all. go to create new partition and make sure it covers the entire disk, you don't want anything to be unusable. then just format to ntfs, select quit and reboot. then reinstall windows

---

### Post by ananbehh on 2009-09-08
I only can creat one ntfs, I left with one more partion , /dev/sda2 extended, and it has a Key next to it LOCKED, what should I do with it..

---

### Post by ananbehh on 2009-09-08
I got the gparted live Cd, when i try to boot i get the same error "
 
Grub loading stage .5.
Grub loading, please wait... 
Error 17

---

