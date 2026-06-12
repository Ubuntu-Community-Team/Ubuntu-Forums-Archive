---
title: "Drive to drive copying slow"
date: 2010-04-26
forum: Hardware
---

### Post by Frogging101 on 2010-04-26
I have 1 WD 500 GB drive, and another WD 1 TB drive. The 500 GB contains Windows 7 and the 1 TB is for backup. They are both hooked up by SATA. DMA is enabled in BIOS for both of them. I am trying to copy 153 GB from the 500 GB to the 1 TB drive. It starts at about 70 mb/s, then after a while goes down to 4 mb/s. It has been copying 6 hours and is not done.

Both partitions involved in the copying are NTFS. I think the problem may be that NTFS to NTFS in Ubuntu isn't very good. Would it help to format the 1 TB to another filesystem (One that is compatible with Ubuntu and Windows)? I can't use Windows because it will not boot.

---

### Post by Frogging101 on 2010-04-26
Bump... !!! Need answer !!! This is unacceptable !!!

---

### Post by 2hot6ft2 on 2010-04-26
This seemed to at least double the speed for me, usually much more than that but at least double.
Right click on the top panel and select Add to Panel
Select CPU Frequency Scaling Monitor
Click Add then Close
Left click on the new applet in the top panel

Select either On Demand or Performance.
Or you can choose the frequency you want the CPU to run at.
You will have to unlock it with your password (naturally). And Authenticate.

By default it's set to power saving.

That's it. Slow usb transfers are a known problem.

---

### Post by Frogging101 on 2010-04-26
It is a SATA drive, and I doubt that the CPU is the problem. I will try it anyway. Thanks for the reply.

EDIT: CPU freq. scaling not supported.

---

### Post by 2hot6ft2 on 2010-04-26
Also krusader is a dual panel file manager and it seems to transfer files a lot faster than nautilus does. It has many more features as well like directory synchronization.
Tools > Synchronize Directories
[Click this to install krusader]("apt:krusader")

It will be in
Applications > Accessories > Krusader

---

### Post by Frogging101 on 2010-04-26
Thanks, I will try it and let you know.

---

### Post by 2hot6ft2 on 2010-04-26
> **Frogging101 said:**
> 
EDIT: CPU freq. scaling not supported.
Bummer. That's too bad because it does work. I have transferred files and changed it back and forth and watched the speed change accordingly.

Like I said you're not alone. Click Ubuntu Forums link at the top left of the forum and on the right put "slow file transfer" with the quotation marks in the search and hit Enter. You'll find a lot of threads on it.

[There's also this option]("http://ubuntuforums.org/showpost.php?p=8854959&postcount=3")

---

