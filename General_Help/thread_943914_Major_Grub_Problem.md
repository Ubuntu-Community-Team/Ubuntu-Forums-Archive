---
title: "Major Grub Problem"
date: 2008-10-10
forum: General Help
---

### Post by windux on 2008-10-10
i have been a windows user for many years. recently however, i decided to give ubuntu a try. since i'm not too great at command lines, i downloaded the .iso of the live cd, and then burned it and booted from it.

i did a check to see if any of the files on the disk were corrupt, but they were not, so i installed ubuntu. the version i have is hardy heron (8.04).

my setup is as follows: i have 2 hard drives. one is a sata hard drive, and the other hard drive is an ide hard drive with an ide to sata converter (both windows xp AND ubuntu disks recognize the presence of this hard drive, and both are able to edit partitions on it). the sata drive is 160 GB, while the IDE drive is 40 GB. on the sata drive, windows xp professional is installed. the ide hard drive is empty, and i want to install ubuntu on it.

since i'm not good at command lines, i used the live cd to install. i did it several times, and in many many different ways, all of which have not worked.

my first attempt was installing ubuntu using the guided install onto the 40 gb drive. however, ubuntu gave me an error: grub loading stage 1.5, a please wait, and then an error 18. this first attempt was done with the "boot loader" under "advanced" of the live cd (not the alternate cd, which i don't have) set to hd0. this first attempt prevented me from even booting into windows. whenever i turned on my computer and didn't have a boot device that was prioritized ahead of my hard drives inserted, the system would simply display that error and do nothing. all i could do was hit power.

since windows xp pro was unable to start, i inserted my xp disc and did a system restore to fix the master boot record. this worked, and windows was able to start again. i then deleted the partitions that ubuntu had created on my 40 gb drive so i could start over. i popped in my ubuntu disc again, and did a manul setup. this was my secon attempt. since ubuntu refused to let me continune unless i set one of the partitions as root (/), i made one partition for swap (2 GB), and another partition consisting of the rest of the space (38 GB). both partitions were formatted as ext3. there was no mount point selectable for the swap partition, while the larger partition's mount point was / (there was no partition with a mount point of /boot in this attempt). again, this failed. this time, i got another grub error: "grub loading stage2read error". for this second attempt, i installed the boot loader into the swap area.

for the third attempt, i did another manual setup, with a 500 MB partition that had a mount point of /boot, a 2 GB partition set as the swap area, and the rest of the space (about 37 GB) in another partition with a mount point of /. i installed the boot loader into the partition with a mount point of /boot this time. once again, i got the error "grub loading stage2read error".

after this third attempt, i installed gag, the open source graphical boot manager in an attempt to salvage the situation. i got the error message "sector boot not found or invalid" for all variations of installing ubuntu except in the cases where i selected from gag the partition to which the boot loader had been installed by the live cd. when i selected this partition correctly, then i would get the error "grub loading stage2read error".

i messed around with my bios and changed the boot order of my hard drives. i set the 40 GB drive to boot before the 200 GB drive. all this did, however, was change the error to a stage 1.5 error.

the jumper setting on my 40 gb drive is set to cable select. if i set it to slave, the motherboard won't even recognize it. the motherboard will also recognize it if the jumper is taken out altogether. this seems to be the result of me using an ide to sata converter.

i am extremely frustrated by all of this. i really want to give linux a chance, but it just has not cooperated with me so far. i've already spent 2 days on it trying out these various possibilities. please..does anybody have any suggestions for me or have i just wasted a cd buring the livecd image? :( needless to say, i am extremely frustrated at this point. i had originally intended for ubuntu to be a complete substitute for windows, but now it seems i can't even get it to boot! thanks for any comments/help that you can give me!

---

### Post by caljohnsmith on 2008-10-10
It might be that you simply have a problem booting your IDE drive, and that would mean it doesn't matter what OS or boot loader you put on the IDE drive; that would be a BIOS issue, but we don't know yet if that is the case. How about we reinstall Ubuntu to your IDE drive and make sure that Grub gets installed to that drive, and not your SATA drive like what happened before; then we can more easily troubleshoot any booting problems you may have with the IDE drive. 

So boot your Ubuntu Live CD again, start up the installer, select "manual" for the partitioning phase, and you'll need to set up at least two primary partitions: one for the Ubuntu main install which will have a root or "/" mount point, and then a swap partition which is mounted as swap. Just make sure the Ubuntu partition comes first, then the swap, and then you can create any extra data partitions if you like. Once you do that and continue to the final step of the install, click the "advanced" button and make sure you tell Grub to install to either /dev/sda or /dev/sdb, *whichever is your IDE drive*. If you are unsure about which drive is the IDE one, you can pull up a terminal (applications > accessories > terminal), and do:
```
sudo fdisk -lu
```
And that will show your drives and partitions. 

I'm going mostly from memory about the steps involved in the Ubuntu installer, so if I missed something and you have questions, of course be sure to ask. Otherwise, let me know if you can get that far, and then we can troubleshoot any booting problems you might have. :)

---

### Post by mkokotovich on 2008-10-10
Also, 8.04 gave me problems with booting/installing on one computer I had.  8.04.1 fixed it though.  I would make sure you have the 8.04.1 release.

---

### Post by windux on 2008-10-10
Edit: i do have the 8.04.1 release. sorry for omitting the last digit.

i guess you're right that i could be having a problem booting the ide drive. i had initially assumed that it would be bootable since both linux and windows cds recognized the presence of the drive at least.

one of the variations i tried was installing ubuntu to the ide drive with manual for the partitioning phase. one has the root as the mount point and the other one is just a swap partition. i've even tried to install the boot loader to both the swap partition and the one with the root as the mount point. i got either the grub stage 1.5 error or stage 2.0 error.

since the problem was there even when i installed exactly as you described, i booted ubuntu off the livecd and typed in "sudo fdisk lu". here is the output for my current installation:

ubuntu@ubuntu:~$ sudo fdisk -lu

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xabcdabce

Device      Boot   Start    End      Blocks      Id     System
/dev/sda1   *      63     390700799  195350368+  7      HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000596f3

Device Boot     Start     End        Blocks     Id    System
/dev/sdb1       63        74862899   37431418+  83    Linux
/dev/sdb2       74862900  78156224   1646662+   5     Extended
/dev/sdb5       74862963  78156224   1646631    82    Linux Swap / Solaris

ubuntu@ubuntu:~$

please help...i really like ubuntu based on what i've seen from the livecd, and i would like to get it to work.

---

### Post by louieb on 2008-10-10
Since your new to dual booting and the GRUB boot loader can be confusing at first. There is a tool  called [Super Grub Disk]("http://forjamari.linex.org/projects/supergrub/"). Its good at configuring GRUB to set up a PC to dual boot. 

Your fdisk output looks just like it should if you used the default partition options.  Now it just a matter of getting GRUB to find both OSes and boot them. 
 Good Luck

 [IDBS on SuperGrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---

### Post by windux on 2008-10-10
i have downloaded, burned and installed the super grub disk. however, it's giving me either error 15 or error 25 depending on what options i try. i failed to boot to ubuntu linux, and the restore options didn't work. i did successfully boot to windows using super grub disk, but i am already able to boot to windows anyways. there are a lot of options and i tried most of them, but i could be missing something. is there anything a specific procedure i should do on the super grub disk?

please help! by now i've reinstalled ubuntu in different ways about 10 times already. i really want to get it to work.

---

### Post by louieb on 2008-10-11
The Ubuntu installer  is usually pretty good at setting up a dual boot. And super grub can fix most dual boot problems. But its time to use the grub> command prompt.  It may be a problem with using an ide drive with a sata converter so.  

1st unplug your windows drive then set your Ubuntu drive to be 1st in the boot order.

Boot the Ubuntu live CD and open Applications>Accessories>terminal

then get a grub prompt  
```
sudo grub
```now let grub find itself on the hard disk.
```
find /boot/grub/stage1
```the fdisk output tell me it should return** (hd0,0)**
if not then theres a problem. Let me know what it returned.
if it does then enter 
```
root (hd0,0)
```does not return anything just enter
```
setup (hd0)
```This should return a success message. if not then there is a problem. 
leave the grub> prompt
```
quit
```If it returns the success message. reboot the computer 

You should now get the grub menu. Select Ubuntu and see if it works.

---

### Post by windux on 2008-10-11
here are my results:
when i type "sudo grub", i get a "grub>" command prompt.

next, i tried "find /boot/grub/stage1". i get the message "Error 15: File Not found".

since it didn't return (hd0,0) as it should have, i tried "setup (hd0)". i got "Error 12: Invalid device requested"

can you tell form this what's wrong? if not, please tell me what i should try next and i'll gladly do it asap. thanks! i'm open to any suggestions or comments right now that could help me resolve the issue.

---

### Post by caljohnsmith on 2008-10-11
OK, from the Live CD, do this:
```
sudo dd if=/dev/sdb bs=512 count=1 2>/dev/null | strings | grep -ie grub -ie "operating system"
sudo dd if=/dev/sdb bs=1 skip=1049 count=2 2>/dev/null | hexdump
sudo mount /dev/sdb1 /mnt
ls -lR /mnt/boot
```
Please post the results, and that will give us a clearer picture of whether you have Grub properly installed. :)

---

### Post by windux on 2008-10-11
do i need to type "sudo grub" before i type those?

also, should i put in each line separately or should i copy and paste the whole thing into my terminal?

assuming that i should put in each line one at a time without typing "sudo grub" (i see ubuntu@ubuntu:~$ in front), the results are as follows:

------------------------------------
the first line gives:

"Error loading operating system"
"Missing operating system"

the second line gives:
0000000 0000
0000002

the third line gives:
(the third line didn't give me any message. it just showed the next ubuntu@ubuntu:~$ to prompt me for another command)

the fourth line gives:
-rw-r--r-- 1 root root    422667 2008-06-18 18:11 abi-2.6.24-19-generic
-rw-r--r-- 1 root root     80049 2008-06-18 18:11 config-2.6.24-19-generic
-rw-r--r-- 1 root ubuntu 7888264 2008-10-09 00:47 initrd.img-2.6.24-19-generic
-rw-r--r-- 1 root root    103204 2007-09-28 10:06 memtest86+.bin
-rw-r--r-- 1 root root    905146 2008-06-18 18:11 System.map-2.6.24-19-generic
-rw-r--r-- 1 root root   1920472 2008-06-18 18:11 vmlinuz-2.6.24-19-generic
------------------------------------

if i needed to type "sudo grub" before using any of these commands or if i needed to put all 4 lines in at once, please let me know and i'll do them over. but if these were unnecessary, then the results are above. i'm sure the experts in the community can read a lot more into them than i am.

---

### Post by caljohnsmith on 2008-10-11
OK, that explains it; when you installed Ubuntu, you didn't install Grub at all. You still have your Windows boot loader in the MBR (Master Boot Record) of the sdb drive, and also you don't have a /boot/grub directory with all the necessary Grub files. 

How about reinstalling Ubuntu, but this time when you get to the final stage of the installation, click on the "advanced" button, and tell Grub to install to /dev/sdb (not /dev/sdb1 or anything else). That will probably be all it takes to fix your problem. If you run into problems or have questions during the reinstallation, don't hesitate to ask. Otherwise let us know how it goes. :)

---

### Post by windux on 2008-10-11
ok, i'll do it over again. i'm doing a "Guided - use entire disk" on the sdb drive again. nowhere in the install, however, do i see the word "grub", so i am a bit confused. when i click on the button "advanced", i see a checkbox labelled "install boot loader" and then a dropdown menu for me to choose the device for boot loader installation. i assume that grub must be the boot loader it's talking about? anyways, with these settings, i will post back my results. with any luck, i'll be able to use the installed ubuntu soon. i've already explored the livecd a lot and i really like it.

---

### Post by windux on 2008-10-11
ok, i have an update on the situation. i reinstalled ubuntu exactly as you described, and i did it using the guided install. after i take the cd out of the drive and restart my computer, i boot directly into windows; in fact, i see no indication ubuntu was ever installed in that drive.

what i did at this point was to change the boot order in my bios. i put my 40 GB drive ahead of my 200 GB drive. this time, i did see something. it gave me the following error message:

"Grub Loading stage1.5Read Error"

given the steps i've taken so far, what could this possibly mean?

---

### Post by caljohnsmith on 2008-10-11
That's great news, we're making progress. It looks like you may have some issues with your Ubuntu drive though, because for some reason it looks like Grub didn't get properly installed to the MBR. Try following these steps to make sure Grub is installed correctly to the MBR (each line is its own command, copy and paste individually like you did before, but don't copy the grub> prompt):
```
sudo grub
grub> find /boot/grub/stage1

```
That should return your Ubuntu partition in the form of (hdX,Y) where X and Y are numbers, for example (hd1,0), but use whatever it returns as follows:
```

grub> root (hdX,Y)
grub> setup (hdX)
grub> quit
```
And post the output for all the above commands. Also please post the output of:
```
sudo fdisk -lu
```

---

### Post by windux on 2008-10-11
here is my output for those commands

--------------------------------------------
find /boot/grub/stage1:
 (hd1,0)
--------------------------------------------
root (hd1,0):
(no output)
--------------------------------------------
setup (hd1):
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/boot/grub/stage2
/boot/grub/menu.lst"... succeeded
Done.
--------------------------------------------
sudo fdisk -lu:
Error 27: Unrecognized command
--------------------------------------------
sudo fdisk -lu (in the ubuntu command prompt as opposed to the grub command prompt):
Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders, total 390721968 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xabceabce

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   390700799   195350368+   7  HPFS/NTFS

Disk /dev/sdb: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders, total 78165360 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000596f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63    74862899    37431418+  83  Linux
/dev/sdb2        74862900    78156224     1646662+   5  Extended
/dev/sdb5        74862963    78156224     1646631   82  Linux swap / Solaris

Disk /dev/sdg: 4043 MB, 4043308544 bytes
255 heads, 63 sectors/track, 491 cylinders, total 7897087 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x91f72d24

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *          63     7897086     3948512    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(490, 254, 63) logical=(491, 145, 37)
--------------------------------------------

---

### Post by windux on 2008-10-12
i just wanted to add that i tried booting again after those series of commands, but it still isn't working. is there something i'm missing?

---

### Post by caljohnsmith on 2008-10-12
So are you getting the exact same Grub error about loading stage1.5? 

According to those commands from your post #15, Grub installed perfectly to the MBR of your Ubuntu drive. I think it is highly likely at this point you have a BIOS issue booting your Ubuntu drive. I would recommend going into your BIOS and changing your HDD settings one by one, and reboot each time you change a setting to see if it makes any difference; I would also write down the original settings of anything you change so you can revert back if necessary. For example, you may see some HDD settings related to LBA, CHS, RAID, AHCI vs. IDE, etc; those are the ones you would want to change.

---

### Post by windux on 2008-10-12
thanks for the reply! i've been waiting 34 hours for one XD

anyways, yes, when i change the boot order so that my ubuntu hard drive is first, i get the following error:

GRUB Loading stage1.5Read Error

i'll try messing around with my bios as you suggest. at this point i'm dying to get this thing to work.

---

### Post by windux on 2008-10-12
wow! i actually got to the boot menu!!! it shows 4 options now in a menu that i can choose from. the first one is basically ubuntu kernel generic (it shows 8.04.1). the second one is like the first one with the word "recovery" added, and the third one is memtest86+. it also shows my windows xp installation under "other operating systems". however, the problem is that when i select any of the ubuntu choices, i get the following:

"Error 17: Cannot mount selected partition"

have i made progress? what is wrong now?

---

### Post by caljohnsmith on 2008-10-12
> **windux said:**
> however, the problem is that when i select any of the ubuntu choices, i get the following:

"Error 17: Cannot mount selected partition"

have i made progress? what is wrong now?
Yes, that's great news, getting Ubuntu to boot now should be easy. When you get the Grub menu on start up, select the first Ubuntu entry, press "e" to edit it, select the line that says "root (hdX,Y)" where X and Y are numbers, press "e" to edit it, change it to "root (hd0,Y)", press return to save the change, then press "b" to boot. Based on the info you gave, I think that should be all it takes to boot Ubuntu. Note that the above change is not permanent, so you'll need to modify your menu.lst to make it permanent.

So if it works, when you get into Ubuntu, just do:
```
gksudo gedit /boot/grub/menu.lst
```
And change the line that says "#groot=(hdX,Y)" to:
```
#groot=(hd0,Y)
```
Also, find your Windows entry in the menu.lst, and change it to:
```
title	   Windows XP
root       (hd1,0)
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader +1
```
Save, quit gedit, then run:
```
sudo update-grub
```
And you should be all set. Let me know how it goes or if you run into problems.

---

### Post by windux on 2008-10-12
thanks so much!! that actually worked! this ends half a week of sheer torture trying to figure out what was wrong, but not having the background to go on it! when ubuntu started up for the first time, i had to double check to make sure the livecd wasn't still in the drive; it couldn't possibly be working!! i guess at this point, i only have a few questions:

first of all, how in the world did you know all this? i googled for hours but none of the solutions i found really matched my situation exactly. now that i finally have linux running, i would like to learn more about it if i could.

also, in the future, if i ever need to reinstall linux, do i have to go through all these steps again, or should the install go smoothly now that my bios settings are configured correctly?

and finally, is there any way i can change grub somehow so that windows xp is defaulted to as opposed to ubuntu? in other words, if i just power on my computer and leave to grab something to eat, it will automatically start xp for me, but if i choose, i can sit down and select one of the ubuntu options to boot into manually.

how do i thank you by adding to the "thanked x times in x posts"? lol..

---

### Post by caljohnsmith on 2008-10-12
> **windux said:**
> thanks so much!! that actually worked! this ends half a week of sheer torture trying to figure out what was wrong, but not having the background to go on it! when ubuntu started up for the first time, i had to double check to make sure the livecd wasn't still in the drive; it couldn't possibly be working!! i guess at this point, i only have a few questions:

first of all, how in the world did you know all this? i googled for hours but none of the solutions i found really matched my situation exactly. now that i finally have linux running, i would like to learn more about it if i could.

A good place to start to learn about Grub is Herman's website:

[http://www.users.bigpond.net.au/hermanzone/p15.htm](http://www.users.bigpond.net.au/hermanzone/p15.htm)

And then there's the official Grub manual:

[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
> **windux said:**
> 
also, in the future, if i ever need to reinstall linux, do i have to go through all these steps again, or should the install go smoothly now that my bios settings are configured correctly?

Fortunately no, you shouldn't have to go through all those steps, because in the end the root of your problem turned out to be a simple issue with your BIOS settings. :)
> **windux said:**
> 
and finally, is there any way i can change grub somehow so that windows xp is defaulted to as opposed to ubuntu? in other words, if i just power on my computer and leave to grab something to eat, it will automatically start xp for me, but if i choose, i can sit down and select one of the ubuntu options to boot into manually.
Sure, open your menu.lst again, and find the line that says "default <number>". Grub's numbering starts with 0 and not 1, so "default 0" means boot the first OS in the Grub menu by default, "default 1" means the 2nd OS, "default 2" means the 3rd OS, etc. Also, you can tweak the amount of time you are given before Grub boots the default OS by changing the "timeout <number>" line, where the number is in seconds.

Anyway, glad its working for you now; cheers and have fun Ubuntu-ing. :)

---

