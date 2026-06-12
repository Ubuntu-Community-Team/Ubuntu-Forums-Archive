---
title: "Uninstall Ubuntu From Windows"
date: 2009-10-13
forum: Installation &amp; Upgrades
---

### Post by sean_whx on 2009-10-13
Hi Guys,

I am wondering if anyone can help me out with uninstalling ubuntu from windows.

I have a new laptop with 140G HD with Windows XP preinstalled. Then I installed Ubuntu within Windows. (I installed ubuntu through cd drive while I was in windows. ) During installation, I can only specify a 30G space for Ubuntu. Then I found that in that way Ubuntu is actually installed within Windows. It doesn't create a new patition for it. Later on I decided to remove it and create a new partition 70G for Ubuntu. I used "Add or Remove Programes" in "Control Panel" and successfuly deleted Ubuntu. But when I reboot my computer, it still asks me to choose which OS to boot between windows and ubuntu, even Ubuntu is not on my computer now.... 

I guess this is related to GRUB or MBR? Could someone give me some hint pls?

As of now, I have already created a 70G partition and installed Ubuntu on it. Now my computer works weird. When it starts, it first asks me to choose a OS between Ubuntu and windows, If I choose Ubuntu it boots correctly. But if I choose windows, it will then asks me to choose between windows and ubuntu again. Apparently the second ubuntu is already removed from windows. 

Any help is highly appprecited. 

Thanks
Sean

---

### Post by ajgreeny on 2009-10-13
I've not used wubi ever, but I think the option of which OS to boot is included in the windows boot.ini file, but I am not totally certain.  Try backing up the current version, then edit out any reference to ubuntu from it and try a reboot.  If you can't get anything to boot after that you can restore the backup version using the ubuntu live CD, by mounting the windows partition and renaming the two files.  You boot.ini file should have more or less the following in it:-

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect 

Any extra lines can be deleted.

---

### Post by physeetcosmo on 2009-10-13
> **sean_whx said:**
> When it starts, it first asks me to choose a OS between Ubuntu and windows, If I choose Ubuntu it boots correctly. But if I choose windows, it will then asks me to choose between windows and ubuntu again. Apparently the second ubuntu is already removed from windows. 

You can insert your Win OS Disk and select to "Repair Previous Installation" which also does an "update" or "clean" of the boot.ini file automatically. It's fairly smart (for Windows) as i have done the same thing you are doing, except i had dual-booted the two OS's until i went strictly with Ubuntu.

May i ask what program you still use in Win that you can't run in Ubuntu? Or find an alternative?

Good luck!:)

---

### Post by raymondh on 2009-10-13
Hi Sean,

Here is the wubi guide.  You have to manually edit the boot.ini file in windows and remove the WUBI-related line.  Only the WUBI related line or you risk losing the boot into windows.

[https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?](https://wiki.ubuntu.com/WubiGuide#How%20do%20I%20manually%20uninstall%20Wubi?)

What I think is happening .....

Now that you installed ubuntu in it's own partition, GRUB detects both and boots your choice.  The problem you have when choosing windows is/may be because you still have the WUBI-related install in the boot.ini file.  

Boot into windows ... look for your boot.ini file ..... manually delete JUST THE WUBI-related lines (per the wubiguide)

Just in case you make a mistake when editing the boot.ini file, kindly back-up first your valuable files.

Regards,

---

