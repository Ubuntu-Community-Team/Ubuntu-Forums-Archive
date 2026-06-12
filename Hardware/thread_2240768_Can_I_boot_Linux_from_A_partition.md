---
title: "Can I boot Linux from A partition?"
date: 2014-08-22
forum: Hardware
---

### Post by firas2 on 2014-08-22
Good Day

I was running Linux In a virtual machine , to test it out , and now that I know I will stick with it, So I decided to install it and run it from a usb3 , But still not happy because it is running slow , and I have a fast pc , 16gb DDR3 (1600) and Core i7- 4770K processor

I have many free Partitions , First Question can I boot Linux from a Partition ? and how [IMG]http://forums.linuxmint.com/images/smilies/icon_biggrin.gif[/IMG]
 ... Second can I backup mu Linux on my usb and move it to the new place ?? or do I have to start all over again ??

your help is much appreciated

many thanks

---

### Post by yancek on 2014-08-22
Yes you can boot it from a partition but there are some caveats.  First off, what else do you have for an operating system?  If you had another Linux system with its bootloader in the master boot record, you could install the new bootloader to its partition and boot from the first system.  If you are not using mbr to boot but uefi/GPT partitioning that is a different situation.  It would be useful if you indicated whether you have another operating system and if so which one and if it is windows, which windows.

---

### Post by firas2 on 2014-08-22
> **yancek said:**
> Yes you can boot it from a partition but there are some caveats.  First off, what else do you have for an operating system?  If you had another Linux system with its bootloader in the master boot record, you could install the new bootloader to its partition and boot from the first system.  If you are not using mbr to boot but uefi/GPT partitioning that is a different situation.  It would be useful if you indicated whether you have another operating system and if so which one and if it is windows, which windows.

Hello yancek

Thank you for helping out , here is my system  and Partitions 

[COLOR=#000000]**[FONT=verdana]operating system! 764X ultimate&#65279; [/FONT]**[/COLOR][B][COLOR=#000000][B]Stable @4.5 :)
Processor: Intel ® Core i7- 4770K processor
Gigabyte GeForce GTX 760 OCWF3X,2GBDDR5
Maximum memory : 32GB / on board 16gb DDR3 1600 Fan:Scythe Mugen 4 (SCMG-4000)/Cougar Power 700 W
Memory clock : 1600 MHz DDR3, CL10 9-9-9-24
SSD : SAMSUNG SSD 840 PRO 128GB
Motherboard: MSI Z87 -G45 GAMING ATX
Case: Cougar Evolution 6GR1B black
HDD: WD Caviar Green 2TB SATA 6Gb / s
Network: Gigabit Killer E2205,Chipset: Intel Z87 Express
[/B][/COLOR]

[/B][http://i.cubeupload.com/BN6rfV.jpg](http://i.cubeupload.com/BN6rfV.jpg)
All the one's with green arrows are free , and good to use , C/  is full as u see and I am runing windows 7 as a raid 1  on 2 SSD's  so I really Dont want to touch C/ 
if this any help 

thank U

---

### Post by yancek on 2014-08-22
You have a number of options as to where you can install Linux.  Since you are posting at an Ubuntu forum are you planning to install Ubuntu or one of its derivatives?

> Second can I backup mu Linux on my usb and move it to the new place ?? or do I have to start all over again ??

Not sure what that means.  Do you currently have some Linux distribution installed?  You can easily backup syste and/or data files to another drive/partition and there are numerous ways to do that.  The image you posted doesn't tell us anything about the filesystems on any partitions.  It would probably be more useful if you posted the information from a Linux system, on a Live CD/flash drive.  If you have one boot it and run the command:  sudo fdisk -l(Lower Case Letter L in the command).  You use sudo if it Ubuntu and some other distributions, don't know what you have.  If you have GPT partitioning, you may get better results with:  sudo gparted.  Post the output here.

---

### Post by firas2 on 2014-08-22
Hello yencek

sorry for the late  respond i was out shopping for a SSD :)  ,,  I did get other help and did find a website that explains every thing on how to do what i want to do,  But I went out and Got me a 128gb ssd  it was on sale :) :)   , so i will just install Linux on there and be happy ,,

I can explain more ,, as I mentioned in my first Post  my second install of linux is on a usb ,, but it is slow very slow and not happy with it,,  But I did some work and conkys and  and  ,, so this is why i decided to find a way to  first how can i back up every thing and second  i should install it either on a partition or a new hdd/ssd  what ever comes first :) 

hop this clears things up     ,,  and ur right  about the UEFI  But lucky me my windowloader is .EXE     

Can u please recommend any way to back up the linux of my usb  ??

many thanks

---

### Post by yancek on 2014-08-22
If you are installing Ubuntu 14.04, click on the System Settings icon in the left panel, the gear/wrench icon.  Open it and on the bottom left you will see a Backup icon.  Just click that and review and select whatever options you want.  Ubuntu isn't my primary system so I back up from another OS so I haven't used this.  I don't see why you would have any problems with it though.

---

### Post by firas2 on 2014-08-24
PROBLEM SOLVED :D :D

Well ever since i removed the new ssd , my pc wont boot normal , it says missing MBR , so I was going a little crazy thinking I lose every thing on my windows . But no it lookes like every time I want to boot into windows I must change boot order , so I said to my self this means I can put back the new ssd with linux installed on it and every thing should work ,,, and It Did :D

So now every time I boot Im into Linux , and if i want windows I just change the boot order 

ya ya ya ya finally

Problem 
=======================

Linux KDE installer kept on crashing for some odd reason , on a new ssd

Solution 
=====================

took out the ssd put it in a old laptop install linux 

took the ssd back to desktop and Boom ur up and running 

for any one who Might run into this in the future 

also it looks Like u can do the same thing By removing ur old windows HDD ,, install linux on the separate HDD ,, put every thing back together and Boot , change boot order

but backup just in-case something goes wrong :D :D
thanks

---

