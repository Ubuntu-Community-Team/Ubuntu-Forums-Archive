---
title: "Fix MBR"
date: 2009-09-22
forum: Installation &amp; Upgrades
---

### Post by roajames on 2009-09-22
I have installed ubuntu 9.04 but have apparently loaded the ubuntu boot loader on my XP disk.(drive 0). Ubuntu is on drive 1, with 2 partitions named unbuntu(78GB) and Docs(298GB) On startup, it does give me the option to boot from ubuntu or Xp. The problem is now when i try to boot into my XP, it can't. Boots into ubuntu is fine, and i cant find my XP files when i am in ubuntu. Can i fix the XP MBR? Will it rewrite the MBR to reflect as XP? Or any other suggestions is very much appreciated?
:(
james

---

### Post by stlsaint on 2009-09-22
yes...if you have a xp disc you can reinstall xp to the MBR... then you can install Grub to the ubuntu hdd(hd1)! please see signatures below on various help with grub or just post back for specific howto help!!

---

### Post by roajames on 2009-09-22
thanks for your reply, looks like i can't find my XP Pro CD my original XP Pro was an SP3, moved location so dont know where it is, any suggestions please? Any other way of fixing the MBR of my XP? Also why is it that on start up there is the option of ubuntu and xp but i can't boot into my XP? Please help!!!

---

### Post by Rab22 on 2009-09-22
> **roajames said:**
> I have installed ubuntu 9.04 but have apparently loaded the ubuntu boot loader on my XP disk.(drive 0). Ubuntu is on drive 1, with 2 partitions named unbuntu(78GB) and Docs(298GB) On startup, it does give me the option to boot from ubuntu or Xp. The problem is now when i try to boot into my XP, it can't. Boots into ubuntu is fine, and i cant find my XP files when i am in ubuntu. Can i fix the XP MBR? Will it rewrite the MBR to reflect as XP? Or any other suggestions is very much appreciated?
:(
james

I'm a bit confused by this. You can load into ubuntu just fine, but you can't load Windows XP? 

What does your grub config look like (menu.lst inside /boot/grub). I'm wondering if your XP config reference is incorrect.  As long as GRUB is running, I don't see any reason why you shouldn't be able to load into Windows XP.

Ensure that your rootnoverify reference is correct -- if you are using /dev/sda1 it'll be (hd0,0). 

You probably can't access your files from ubuntu because the partition isn't mounted.  You can mount it by executing a mount command on the /dev device.  For example, 
```

sudo mount /dev/sda1 /mnt

```
This command will mount the filesystem of /dev/sda1 onto /mnt so you can access the data.

You can remove this reference by unmounting the device
```

sudo umount /mnt

```


Hope this helps!

---

### Post by roajames on 2009-09-22
Rab22 thanks for your rely. I am also confused, this is not the first time i am loading ubuntu and have 2 systems running both XP Pro and unbuntu 9.04, and both systems working just fine as it should. On the system that is problematic, what i noticed is that when I tried to load ubuntu, everything came up fine, accept that it took some time to find that the Disk 0 had an operating system(XP), initially it showed as "this partition has got no operating system" and after about 6 secs or so, it came up with showing the disk 0 as  with XP(sda1),(colored blue) /dev/sda2(colored green).
Did the install as :install side by side" indicating Disk 2 in the drop down menu and continued as the instructions.
However, when it came to "where do you want to install the boot loaded, indicated it as "disk 0" and after unbuntu install completed, booted up - thats when i noticed that i cant boot into XP.

---

### Post by Rab22 on 2009-09-24
> **roajames said:**
> Rab22 thanks for your rely. I am also confused, this is not the first time i am loading ubuntu and have 2 systems running both XP Pro and unbuntu 9.04, and both systems working just fine as it should. On the system that is problematic, what i noticed is that when I tried to load ubuntu, everything came up fine, accept that it took some time to find that the Disk 0 had an operating system(XP), initially it showed as "this partition has got no operating system" and after about 6 secs or so, it came up with showing the disk 0 as  with XP(sda1),(colored blue) /dev/sda2(colored green).
Did the install as :install side by side" indicating Disk 2 in the drop down menu and continued as the instructions.
However, when it came to "where do you want to install the boot loaded, indicated it as "disk 0" and after unbuntu install completed, booted up - thats when i noticed that i cant boot into XP.

It sounds as though you correctly followed the install procedures. I'm wondering whether the lag you report between the installer recognizing your Windows XP partition on /dev/sda1 (hd0) caused the GRUB installer to not put a reference in the GRUB menu. 

When booting, are you presented with a Windows XP option? If so, can you look in /boot/grub/menu.lst (you can open this in Gedit) and see if at the bottom you have a reference similar to this, 

```

title		Windows XP (loader)
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1

```

If not, you may want to consider adding these lines (change ",0" to your correct partition on sda1 (hd0)) and try rebooting.

---

### Post by roajames on 2009-09-24
> **Rab22 said:**
> It sounds as though you correctly followed the install procedures. I'm wondering whether the lag you report between the installer recognizing your Windows XP partition on /dev/sda1 (hd0) caused the GRUB installer to not put a reference in the GRUB menu. 

When booting, are you presented with a Windows XP option? If so, can you look in /boot/grub/menu.lst (you can open this in Gedit) and see if at the bottom you have a reference similar to this, 

```

title        Windows XP (loader)
rootnoverify    (hd0,0)
savedefault
makeactive
chainloader    +1

```If not, you may want to consider adding these lines (change ",0" to your correct partition on sda1 (hd0)) and try rebooting.
Hi Rab22 thanks again, it may soon come to time when someone may boot me out of this forum for being a dumb stupid clown and troubling everyone...to answer your question, no i dont have any boot option, on startup it goes straight into windows - yup, no dual boot option....me getting very frustrated mate. My other 2 systems, well i have to say it works perfect - i get the option of ubuntu and other system(windows) - damn i have been fighting with this particular problematic system sine monday, worst off - i actually recommended ubuntu to my client, after he had tested out one of my systems with dual booting...haha i am the clown, please heeellllllppppppppp!!!!!!!!
 :cry: ](*,)
james

---

### Post by oldfred on 2009-09-25
Booting is from the first hard drive in BIOS. Did you do a windows fix disk to put windows back in the MBR or switch boot order in BIOS?

Supergrub is one of the easist ways to fix booting. I always have a current supergrub disk handy whenever I modify my system:
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)

You can follow one of the guides on reinstalling grub from a live CD. One of many available:
[http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore](http://ubuntuforums.org/showthread.php?t=24113&highlight=grub+restore)

 A bit more complecated is to keep the windows boot in the windows drive but make it the second drive in BIOS (sda2 or hd1 in grub). This way if you want to directly boot windows without the Ubuntu drive you can. You put grub in the non windows drive and make it sda1 or hd0 in bios and the first to boot in BIOS. Because windows wants to be the first you have to add map commands in the window grub entry to make windows think it is first.

title        Microsoft Windows XP Professional on sda2
rootnoverify    (hd1,0)
savedefault
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader    +1

---

### Post by roajames on 2009-09-25
Hiya oldfred, thanks for the reply. I have managed to fix the MBR with XP install disk which i manage to find. XP is back to normal without doing a ubuntu re-install yet. Still don't know what i did wrong though, considering i did ubuntu installs as dual boot(XP n Ubuntu) on 2 machines and these 2 are working fine. The setup on my problematic machine now is like this:
(1)80GB SATA 1 drive C - XP PRO (balance free space 27GB)
(2)320GB SATA 2 drive D - MOVI
(3)750GB SATA 3 - 1st partition drive E 98GB - DOCS
2nd partition drive F 245GB - MUSIC
3rd partition drive G 355GB - WEB FILES
I had to reformat (2) and (3) to put back the files that i backed up. I still would like to put ubuntu 9.04 back onto the machine, but am hesitant as i have failed miserably for 5 days ](*,)
I dont want to put unbuntu in XP but wish to make a partition in the 750GB (about 100GB) and install ubuntu in this 100GB.
Please advice/help as to how best to install ubuntu as described above, - ubuntu bootloader will be in the 100GB.
Appreciate your advice.
Thanks - James
:(

---

### Post by oldfred on 2009-09-26
One of the more knowledgeable forum members suggested that every hard drive with an operating system should have that MBR set up even if it is not used. That way if the boot drive dies the second drive is still bootable without having to use a liveCD or USB. Another suggested always putting a 4GB small linux (forgot version) on every drive just to make sure you can get to your data.

If you install Ubuntu to your 100GB partition (may be large) you can at the end use advanced to put the grub into the 750GB MBR. Then in Bios make the 750GB drive boot first. At the time of install the windows was first so the autocreated grub entry for windows will be wrong and need the map commands and changes to the drive number. Drive number to map will depend on whether it is the second - grub 1 or third - grub 2 drive in the Bios boot order.

Since you have your data in added partitions you do not necessarily have to have a separate /home but it still makes it easier to install a new release of Ubuntu, rather than an in place upgrade. With 100GB available you have room for other operating systems if you want to leave space. Ubuntu only needs 10GB and many seem to get by with 15 to 20 with many applications as long as data is in separate partitions.

---

