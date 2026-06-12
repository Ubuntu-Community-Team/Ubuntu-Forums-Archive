---
title: "Stepping up to Ubuntu"
date: 2008-11-17
forum: General Help
---

### Post by emilav on 2008-11-17
Hi everyone.

I have been using windows only for a very long time. Now I want to try Linux, and I was told that Ubuntu one of the best options because it is also easy to use. So UBUNTU it is :P

I have been trying it (LiveCD) and liked it.

Pltaform is: 
IBM R61 8918 5QG
Intel Dual Core 1.8 Ghz
4 GB RAM (upgraded)
NVidia Quadro Something for Graphics
120 GB HDD
I have 2 partitions.
C: for System (Win, now) - 7GB free space 
and D: for Data - 15 Gb free space

Where should I install?
How? I only installed windows once, so that's a scary area for me...
Usually I just ask a friend to do it, but I think it's time to learn how to do it myself.

So please help, guys.

Thanks.

Emil.

---

### Post by volaer on 2008-11-17
If you are using Ubuntu 8.04 CD or 8.10, you will have no problem... simply put the cd in your cd rom (make sure though that your BIOS is set up in CD/DVD Rom Boot first). then a menu options will appear, choose what's the best option that you want to do.:) then it will be interactive and you will have just to answer what it asks.:)


Literally speaking there should be no problem with your installation.:)

---

### Post by frankleeee on 2008-11-17
> **emilav said:**
> Hi everyone.

I have been using windows only for a very long time. Now I want to try Linux, and I was told that Ubuntu one of the best options because it is also easy to use. So UBUNTU it is :P

I have been trying it (LiveCD) and liked it.

Pltaform is: 
IBM R61 8918 5QG
Intel Dual Core 1.8 Ghz
4 GB RAM (upgraded)
NVidia Quadro Something for Graphics
120 GB HDD
I have 2 partitions.
C: for System (Win, now) - 7GB free space 
and D: for Data - 15 Gb free space

Where should I install?
How? I only installed windows once, so that's a scary area for me...
Usually I just ask a friend to do it, but I think it's time to learn how to do it myself.

So please help, guys.

Thanks.

Emil.

Do you want to keep the MS and dual boot or just do a fresh install, these questions will help whoever guides you or posts links,

---

### Post by Kevbert on 2008-11-17
Welcome to Ubuntu. 
I assume you're using XP.
I recommend you use manual patitioning. When you get to the manual option select manual NOT guided. Use 4Gb spare memory on your C drive for the swap (this is used for hibernating/standby and when you need more than 4Gb RAM - virtually never). Use the 15Gb on the DATA drive for your system mount point / formatted ext3. 
The boot partition will be overwritten by the Grub bootloader that comes with Ubuntu. This will give you options to boot either operating system.
Wireless/Ethernet. If you have an ethernet connection and a router it may be worth connecting this up when you install as you will then find it easier to install any additional drivers for wireless (which can be a pain), display adapters etc.

---

### Post by soro2005 on 2008-11-17
You will need more disk space for a permanent solution. You should see whether you can free up another 15 GB, or else think about getting some external storage. You will need at least 10 for your Ubuntu system, and then some free space for more data, etc.

This, of course, unless you want to dump your Windows.

---

### Post by volaer on 2008-11-17
Just a reminder, it is always best to have your pc connected most of the time to the internet for updates. If you will have some problems in your programs in ubuntu, updates will really help you. Hope you will enjoy UBUNTU a lot as I am.:)

---

### Post by emilav on 2008-11-17
Hey!

Thanks for the (very!!) quick replies!

I guess I should have specified. I am using Vista and I want to use both Win and Linux. I am also afraid of being in short of space. I have external storage but I kind of need everything on drive.

I'll have to think some more about this..

edit: Kevbert, can you please explain that a little? :">

---

### Post by geirha on 2008-11-17
Then I suggest you install it with Wubi. That is, instead of booting the ubuntu CD and clicking the install icon, boot into windows, and insert the ubuntu CD. The autorun menu of the CD will give you the option of installing it in windows. That means it will not use your harddrives directly, but use a big file on either your C: or D: as a virtual harddisk. It needs to use at least 5GB, but I recommend you use 10GB or so.

If you get fed up with ubuntu, just boot into windows and uninstall it as any other windows application.

---

### Post by emilav on 2008-11-19
I managed to free some space. Now I have:
C - free space 8Gb
D - free space 27Gb
I will boot with the LiveCD again to check if everything is ok. After that I'm ready to go. I just hope the installation is straight forward.

---

### Post by volaer on 2008-11-19
When you run the cd, just follow the instruction... If you just take time to learn using ubuntu... you will love it... I am about to dump my xp.... very soon.... just backing up my files.:)

---

### Post by hyper_ch on 2008-11-19
Rule 1: ALWAYS HAVE BACKUPS, REGARDLESS OF WHAT YOU DO.

Rationale: Your harddisk may fail any day without giving you warning or something and without you doing anything.

If you follow that rule then go ahead :)

---

