---
title: "Unable to use HDD with bad sectors, how to fix?"
date: 2012-06-07
forum: Hardware
---

### Post by vazduxosbra4kania on 2012-06-07
Hello i am aware that i have bad sectors on my alternate HDD. With Windows 7 i am able to see and use the HDD anyway. With Ubuntu i can see the HDD but when i try to browse it fails giving me the msg that i attached as a printscreen images. Is it possible to fix this issue so i can use my HDD

---

### Post by wilee-nilee on 2012-06-07
If your HD is bad stop trying to use it get another and try to get off the one that is bad what you can.

Use the smart check app in the disk manager to check the HD from the live cd to get a better look at the HD.

---

### Post by vazduxosbra4kania on 2012-06-07
> **wilee-nilee said:**
> If your HD is bad stop trying to use it get another and try to get off the one that is bad what you can.

Use the smart check app in the disk manager to check the HD from the live cd to get a better look at the HD.

Ok Ok i dont mind bad sectors i am using this hd only to keep movies and other not important information. While it is still working i have no intention to stop using it. My question is how can i make it work not only on my windows. Or u are saying that i cant use it on linux,only on windows

---

### Post by wilee-nilee on 2012-06-07
> **vazduxosbra4kania said:**
> Ok Ok i dont mind bad sectors i am using this hd only to keep movies and other not important information. While it is still working i have no intention to stop using it. My question is how can i make it work not only on my windows. Or u are saying that i cant use it on linux,only on windows

You will not get any legitimate advice that is in the realm of continuing to use a bad HD period.

---

### Post by irv on 2012-06-07
There are utilities out here to block off bad sectors and only use the good ones, but to be real honest with you, the drive is going to fail, and fail very soon. Like what was already said, get the data off of it while you can, and then scrap it and get a new one. The price of a new drive will save you many head aches in the long run and the cost of drive have come down in price.

---

### Post by vazduxosbra4kania on 2012-06-07
So from ur words i understand that there is no way to baypass this stupidity not letting me to use my "good" sectors...OMG!!! And btw i am perfectly aware that sooner or later this drive will fail but this is why i have 3 HDD on my comp and this one contains only movies. And another thing, may be this will suprise you but this drive has been working with bad sector for around 10-11 months now and u cant expect me to throw it just cause some1 sais so ;) ;)

---

### Post by ahallubuntu on 2012-06-07
Depends what you mean by "bad sectors."

You can try zeroing out the entire hard drive with a program like DBAN which can write zeros to the entire drive.  (THAT WILL ERASE EVERYTHING ON IT!)  Try [www.dban.org](www.dban.org) and download/burn/boot the CD on the computer with that drive attached.  MAKE SURE you zero out the correct drive!  I would unplug all other drives while you are running DBAN, just to be safe.

After DBAN, check the drive's S.M.A.R.T. health with smartctl (or GSmartControl in Ubuntu).  If there are still pending sector errors, it's not worth using the drive - you're going to keep having issues with files not being able to be read or even freezes in your system while it waits to access a bad part of the drive.

If the drive has only "reallocated sectors" and no "pending sectors" according to S.M.A.R.T., then your can keep using the drive.  These reallocated sectors were bad sectors marked bad by the drive firmware and replaced with spare sectors.  But if the drive is failing, eventually more sectors will fail until you run out of spares.  Then, again, it's time to replace the drive.

---

### Post by wilee-nilee on 2012-06-07
> **vazduxosbra4kania said:**
> So from ur words i understand that there is no way to baypass this stupidity not letting me to use my "good" sectors...OMG!!! And btw i am perfectly aware that sooner or later this drive will fail but this is why i have 3 HDD on my comp and this one contains only movies. And another thing, may be this will suprise you but this drive has been working with bad sector for around 10-11 months now and u cant expect me to throw it just cause some1 sais so ;) ;)

The deal here is that you are wasting the time of the forum, and when it does fail, you will be wasting it again trying to get the stuff off of it.

Use your brain here not your needs beyond everyone else&#8217;s consideration.

You have not even run a smart test yet come on.

Ah and your the bad video poster as well oh boy. Posting bad convoluted videos for setting up stuff, and using the forum for your own needs beyond anybody else&#8217;s consideration it is all a pattern now is it not.

---

### Post by vazduxosbra4kania on 2012-06-07
> **ahallubuntu said:**
> Depends what you mean by "bad sectors."

You can try zeroing out the entire hard drive with a program like DBAN which can write zeros to the entire drive.  (THAT WILL ERASE EVERYTHING ON IT!)  Try [www.dban.org](www.dban.org) and download/burn/boot the CD on the computer with that drive attached.  MAKE SURE you zero out the correct drive!  I would unplug all other drives while you are running DBAN, just to be safe.

After DBAN, check the drive's S.M.A.R.T. health with smartctl (or GSmartControl in Ubuntu).  If there are still pending sector errors, it's not worth using the drive - you're going to keep having issues with files not being able to be read or even freezes in your system while it waits to access a bad part of the drive.

If the drive has only "reallocated sectors" and no "pending sectors" according to S.M.A.R.T., then your can keep using the drive.  These reallocated sectors were bad sectors marked bad by the drive firmware and replaced with spare sectors.  But if the drive is failing, eventually more sectors will fail until you run out of spares.  Then, again, it's time to replace the drive.

Thank you apparently i will have to give it to friends for fix to use it on linux...Well it is not so important. I have many HDDs...

---

### Post by irv on 2012-06-07
Run gparted, unmount the drive select the partition and run check. I am not sure but it might mark the bad sectors. I haven't run this for awhile.
[ATTACH]219363[/ATTACH]

---

### Post by nj_peeps on 2012-06-07
You can also zero out the drive by using dd (THIS TOO WILL ERASE ALL DATA ON THE DRIVE). For example if the drive in question is /dev/sdb the command would be
```
 dd if=/dev/zero of=/dev/sdb
```This will force the drive to write to every sector, allowing the drive to mark any bad sectors (relocating them) it comes across.  Drives also do this under normal use, but will the drive will only know if a sector is bad when it tries to read/write to it 

 You might want to look at the drive's S.M.A.R.T. stats both before and after zeroing it out so you can compare them.  If you see alot of ECC errors, you many need to reseat the data cable, or get a new one, as this can be cause of errors.

---

### Post by vazduxosbra4kania on 2012-06-07
> **irv said:**
> Run gparted, unmount the drive select the partition and run check. I am not sure but it might mark the bad sectors. I haven't run this for awhile.
[ATTACH]219363[/ATTACH]

i am installing gparted now when i have result i will post it but again i will say that the problem are not the fails of the hdd but the fact that i cant browse through it :(

---

### Post by kelvin spratt on 2012-06-07
> **vazduxosbra4kania said:**
> i am installing gparted now when i have result i will post it but again i will say that the problem are not the fails of the hdd but the fact that i cant browse through it :(
Turn smart data of in your bios then you wont get any messages till it runs out of spare sectors.
you could also try to repair it with a program on Hirons boot disk yes it can be done i've done it and after 2 years its still working. But you need to remove all data with 0000000 1st as this also removes any rootkits on the drive

---

