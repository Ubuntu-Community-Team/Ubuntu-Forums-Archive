---
title: "dual-boot ubuntu windows-vista home premium"
date: 2009-08-06
forum: Installation &amp; Upgrades
---

### Post by souse on 2009-08-06
I was able to install Ubuntu 8.04 LTS & 9.04 as a dual-boot. However during installation, it prompted only two options 

1) use entire-disk 
2) manual partition

as manual partition is only for experts. I didn't touch that. 
Also I don't want to give entire-disk to ubuntu as I have Windows vista running and I will take some more time to get comfortable with ubuntu and do away with vista.

I was expecting 3 options as provided in ubuntu pocketguide, but got only two. Is there a way around?
----------

Hi,

I AM A NOVICE NOW!

I am committed to switching to ubuntu after being fed-up with Windows. I used ubuntu pocketguide for reference and tried to install 9.04 alongside windows vista home premium.
I downloaded both 32-bit & 64-bit (as my C2D supports) and changed the boot loader to start ubuntu installation.

With 32-bit, after restarting and using boot item to select CD-ROM, I got only blank screen with _ blinking after a while it tries to load Windows. 

With 64-bit, after selecting it to load from CD-ROM for installation, I was asked to select the language. I chose English and then it goes to a screen when I have 5 options. I chose 'Install ubuntu'...after pressing Enter....the page stays as it is ...for atleast one hour. I also couldn't use F4 F5 or any of the keys. 

I am downloading 8.04 LTS if it can be of help. Pls can any one of you ever encountered this problem / question. Kindly guide me. 

Thanks, Vj

---

### Post by souse on 2009-08-06
Is there a way to allocate only certain disk space for ubuntu and retain vista during installation?

---

### Post by BZF on 2009-08-06
[FONT=Arial][SIZE=1]yes you choose manuel partition, its not for experts its just for setting up the space ubuntu will use[/SIZE][/FONT]

---

### Post by AmerNewbieInDE on 2009-08-07
Being a Vista user myself, if you go to admin tools, computer management, disk management...  you can right click your windows partition and shrink it then create a new partition for your new install to use.

---

### Post by souse on 2009-08-07
I will try the two options suggested and will post result here. I hope it doesn't wipe out my Windows Vista (even though I didn't like it I have to stay with it till I am comfortable with ubuntu)

---

### Post by phillw on 2009-08-07
[SIZE=2]Hi - Have a read thru' here .....

[https://help.ubuntu.com/community/Beginners/FAQ](https://help.ubuntu.com/community/Beginners/FAQ)

Should walk you through the install.

Regards,

Phill.
[/SIZE]

---

### Post by kg84 on 2009-08-07
> **AmerNewbieInDE said:**
> Being a Vista user myself, if you go to admin tools, computer management, disk management...  you can right click your windows partition and shrink it then create a new partition for your new install to use.

Yep - this is the easiest way. When you then go to install Ubu, an option will be there to use the largest free space. Use this - Ubu will then install on the partition you created under windows and dual boot with it.

---

### Post by souse on 2009-08-11
I couldn't succeed with either of the options. 
From Windows > Control Panel > Admin Tools > Disk Management ...the partition request takes long time (> 30 mts) and system just hung.

From Ubuntu, Manual Partition > there is a error on the main hard drive for a bad sector and doesn't allow me to specify new partition space for ubuntu and instead opting to use the entire disk (even under manual partition). I think this could wipe out the windows...which I am not prepared for now. 

I suspend my ubuntu journey now...and wait for my new PC so that I go for all ubuntu !
Thanks for all your support...appreciate it.

---

### Post by Mark Phelps on 2009-08-11
> **souse said:**
> From Windows > Control Panel > Admin Tools > Disk Management ...the partition request takes long time (> 30 mts) and system just hung.

From Ubuntu, Manual Partition > there is a error on the main hard drive for a bad sector ... 
These both give the indication that you have hard drive problems.  Could be a failing drive; could just be filesystem corruption.

Suggest you boot into Vista and run a chkdsk on each of your "volumes".  That should at least take care of any filesystem corruption problem.

---

### Post by souse on 2009-08-27
Hi,

I built new rig with i7-920, gigabyte mobo with 6GB DDR3 RAM. I installed ubuntu 9.04 32-bit on the 1st harddisk and 64-bit on the 2nd harddisk. I installed 64-bit to check if I can use most of my frequently used applications without any problem. So far I didn't face any problem. I may drop 32-bit after a month or so. Unless absolutely necessary I am not planning to install Microsoft Windows. As my kids are only 2yrs now, when they get to know about computers, it will be great to introduce them directly on the linux/open world than windows. Till they come and push me aside from using this computer I am beginning my journey from Novice to Enthusiast /Intermediate. 

So far without any proper knowledge of linux or any OS (I've been user of a computer all this while and getting hands-on only now), I seem to get around the challenges I've faced with ubuntu by luck / reading / posting questions in forums and getting assistance from experts...I hope that the luck continues as I explore more about this open world.

I am not planning to dual boot on my windows laptop. Either leave it as it is or if I am very comfortable, so as my wife, I will change that to ubuntu as well.:P

Thanks, VJ

---

