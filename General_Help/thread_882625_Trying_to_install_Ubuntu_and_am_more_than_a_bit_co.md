---
title: "Trying to install Ubuntu and am more than a bit confused by this!!!"
date: 2008-08-07
forum: General Help
---

### Post by AlkalineNo1 on 2008-08-07
Hi, I've used Ubuntu on and off for a while now, and usually dual booted it with Vista or XP. My main Desktop has 2 copies of vista and one of XP installed, all for various reasons. My question is, will ubuntu install alongside them? I ask because when i have tried i can partition the /home ext3 partition, but the free space left for the swap is aparantly unusable, despite it being 6gb (2x my RAM) Also tried to create the ext3 and swap partitions the simple way using Acronis, but then cant find them to install to from the ubuntu disk.

I am completely stuck here, can anyone help? let me know if you nedd more info. 

Cheers!

---

### Post by ibutho on 2008-08-07
Hi.

You can only have a maximum of 4 primary partitions. What you need to do is create an extended partition before creating /home and then create /home and swap as logical partitions. Also there probably is no need to have such a large swap space. 6GB of swap will simply result in wasted disk space unless you are running memory intensive applications.

---

### Post by ilrudie on 2008-08-07
I agree.  6gb of swap is most likely way too much.  I have 3gb of memory and a 1gb swap and I have never seen swap space used.

---

### Post by aman.agx on 2008-08-07
I have 2 GB memory and I have never seen swap being used. 
However there is one thing I faced while trying to install WINXP. Just posting the experience. see if you have the same problem.

When I tried to install the WINXP it didnt recognise my hard disk. The reason was that the new hard disks have two modes. IDE and RAID. this can be modified in BIOS. XP setup couldnt recognise the RAID mode. so I had to change it to IDE. 

Regards,
Aman

---

### Post by Titan8990 on 2008-08-07
> XP setup couldnt recognise the RAID mode. so I had to change it to IDE. 

This is because you didn't hit F5 before the installer loads to install your RAID drivers via a floppy disk (yes, you heard right, it still only uses floppies).

---

### Post by AlkalineNo1 on 2008-08-07
> 
Re: Trying to install Ubuntu and am more than a bit confused by this!!!
I have 2 GB memory and I have never seen swap being used.
However there is one thing I faced while trying to install WINXP. Just posting the experience. see if you have the same problem.

When I tried to install the WINXP it didnt recognise my hard disk. The reason was that the new hard disks have two modes. IDE and RAID. this can be modified in BIOS. XP setup couldnt recognise the RAID mode. so I had to change it to IDE.

Regards,
Aman


Hi, I actually had this issue on my laptop, however in this instance, I dont have the problem with XP.

I managed to solve the disk issue, but now seem to have a whole host of other problems, i.e. the boot loader for neither windows or ubuntu will load, i may have to simply format now! We shall see!

---

### Post by jimv on 2008-08-07
You can get your Windows bootloader back by putting your Vista cd in and running the fixmbr command in the Recovery Console.

Once you get Vista up and running again, you can use these instructions (which I actually haven't tried, but hey) to use Vista's bootloader to load Ubuntu:
[http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx](http://port25.technet.com/archive/2006/10/13/Using-Vista_2700_s-Boot-Manager-to-Boot-Linux-and-Dual-Booting-with-BitLocker-Protection-with-TPM-Support.aspx)

---

