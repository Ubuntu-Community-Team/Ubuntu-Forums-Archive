---
title: "Deleted Ubuntu partition - GRUB error - cant boot to Win7"
date: 2009-11-11
forum: Installation &amp; Upgrades
---

### Post by j15big on 2009-11-11
Hi everyone. I know I went about doing this the wrong way, but whats done is done :sad:
I had Ubuntu installed on a second hard drive. I deleted the partition which Ubuntu was installed on through Windows 7 system manager. Dont worry, Im not giving up on Ubuntu, Im simply selling the computer. Well, once I deleted the Ubuntu partition, GRUB is giving me an error and it seems any commands I type are "invalid". I upgraded from Vista to Win 7 and of course I dont have the Win7 disk. How can I remove GRUB and get windows booting again? 
 
Thanks
 
PS
I dont think it matters, but both Ubuntu and Win7 are 64bit versions

---

### Post by slakkie on 2009-11-11
You need a windows rescue disk of some sort.

I believe the command you are looking for is chkdsk /mbr or something really similar.

[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)

---

### Post by raymondh on 2009-11-12
> **slakkie said:**
> You need a windows rescue disk of some sort.

I believe the command you are looking for is chkdsk /mbr or something really similar.

[http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm](http://pcsupport.about.com/od/fixtheproblem/ht/repairmbr.htm)

neosmart.net has a windows 7 recovery disc which you can boot into ... and access a command prompt to fix the MBR.

A quick google shows that the site (neosmart) is down or cannot be accessed.  You might want to try tomorrow and download/burn that disc.

Regards,

---

### Post by wilee-nilee on 2009-11-12
> **j15big said:**
> Hi everyone. I know I went about doing this the wrong way, but whats done is done :sad:
I had Ubuntu installed on a second hard drive. I deleted the partition which Ubuntu was installed on through Windows 7 system manager. Dont worry, Im not giving up on Ubuntu, Im simply selling the computer. Well, once I deleted the Ubuntu partition, GRUB is giving me an error and it seems any commands I type are "invalid". I upgraded from Vista to Win 7 and of course I dont have the Win7 disk. How can I remove GRUB and get windows booting again? 
 
Thanks
 
PS
I dont think it matters, but both Ubuntu and Win7 are 64bit versions

If you upgraded you can probably get a ISO of the install from where you got the upgrade. Was this a student upgrade if so Digital River will give you the ISO link. I suspect Digital River is the provider for all the online upgrades. The ISO is the same as a retail purchase the key is just a upgrade key. Check this out.
[http://techpp.com/2009/11/11/download-windows-7-iso-official-direct-download-links/](http://techpp.com/2009/11/11/download-windows-7-iso-official-direct-download-links/)

I got both the .exe and the ISO links and the DVD from Digital River in the student upgrade, I also added the year access to those links which extends the 30 day install limitations in the contract.

---

### Post by jmusso on 2009-11-12
Well I did basically the same thing. I deleted the partition with Kubuntu on it (I installed Ubuntu through Wubi so it was within my windows partition). Upon booting now I just get a Grub error message. I'm booting through Kubuntu live disc and I'm wondering if I can just reinstall grub through the command line in here, or get rid of it all-together. I just want to boot into windows, or get the same tree of options I got if I selected windows before (since I installed thru wubi it brought me to another Grub screen, but only if I picked Windows at the original). I don't think I'll need to use a recovery disc honestly..

---

### Post by wilee-nilee on 2009-11-12
> **jmusso said:**
> Well I did basically the same thing. I deleted the partition with Kubuntu on it (I installed Ubuntu through Wubi so it was within my windows partition). Upon booting now I just get a Grub error message. I'm booting through Kubuntu live disc and I'm wondering if I can just reinstall grub through the command line in here, or get rid of it all-together. I just want to boot into windows, or get the same tree of options I got if I selected windows before (since I installed thru wubi it brought me to another Grub screen, but only if I picked Windows at the original). I don't think I'll need to use a recovery disc honestly..

I am not sure you can install grub without a installed OS, all you have to do is dual boot Ubuntu or Kubuntu what ever you want and you will get grub back and your windows to. Otherwise you have to reinstall the windows bootmanager into the MBR with a recovery disc. If you want Ubuntu install it as a dual boot and remove the wubi and edit the windows boot with msconfig in windows if it still shows Ubunutu there after removal.

It is hard to tell what your actual goal is here. ;)

---

### Post by slakkie on 2009-11-13
> **wilee-nilee said:**
> I am not sure you can install grub without a installed OS

You can, just need a live CD to accomplish this.

See [this page](http://ubuntuforums.org/showpost.php?p=8265807&postcount=5)

You can skip changing menu.lst, and then perform the actions like described.

---

