---
title: "External HDD not being recognized anymore"
date: 2011-11-27
forum: Hardware
---

### Post by mikrowelle on 2011-11-27
I've got a 1 TB external HDD which worked just fine earlier today and now it's not being recognized anymore. My second external HDD which was connected all the time as well is still working.

I've tried connecting it to several USB ports, I've tried rebooting the system with the HD both plugged and unplugged, I've tried if it works on Win7 (which it doesn't)..

Is there any way to check what the problem is? Thanks in forward.. :'(

---

### Post by dabl on 2011-11-27
If you run ```
sudo fdisk -l
``` do you see it on the list?  If not, then you will probably have to remove the drive from its enclosure, and connect it directly to the SATA interface on your computer, if that is possible, as well as to a power connector.  If you can do that, then you can use tools such as smartmontools, testdisk, etc. and check the condition of the hard drive.

---

### Post by mikrowelle on 2011-11-27
Nope.. it's not there. Thanks for the advice!

Now I'll just have to figure out how to open this plastic brick without any visible screws.. :D

---

### Post by 2F4U on 2011-11-27
> **mikrowelle said:**
> Nope.. it's not there. Thanks for the advice!

Now I'll just have to figure out how to open this plastic brick without any visible screws.. :D

Did you look into the log files? They may contain a hint on why it is no longer detected.

---

### Post by mikrowelle on 2011-11-27
You mean with dmesg? If yes, I checked it several times before/after plugging/unplugging it, but nothing changed.

---

### Post by Dale61 on 2011-11-28
What brand is it?

I borrowed a WD 2TB external from a nephew and it worked fine, but a 1.5TB WD I borrowed from the BIL didn't. 

I spent time on google trying to find a fix, but found that some WD drives have been failing due to a bad connection between the drive unit and the external housing.

However, this wasn't the cause of the failure of the 1.5TB; the BIL thought that any old leads would work, and in this case they didn't, because when he got home and plugged it in with the leads that came with the drive, it worked fine.  He has since bought it back here, with the correct leads, and it worked.

Go figure!

---

