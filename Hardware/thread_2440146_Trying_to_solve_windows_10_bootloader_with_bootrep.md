---
title: "Trying to solve windows 10 bootloader with bootrepair"
date: 2020-04-06
forum: Hardware
---

### Post by gabelumayog0509 on 2020-04-06
safe mode, all restore point, deleting updates, all the options in windows 10 bootloader I have tried. Even a bootable usb, I'm still not able to startup windows 10 without the need of reformatting the whole drive. I tried using bootrepair, but it's still not fixed.

Bootrepair report: [https://paste.ubuntu.com/p/GmkBFHVKWC/](https://paste.ubuntu.com/p/GmkBFHVKWC/)

I'm also trying to backup my hard drive using ubuntu but I can't get any luck since every solution I tried gives me an input/output error and I can't seem to access folders in my hard drive.

---

### Post by CelticWarrior on 2020-04-06
> Invalid MBR Signature found.

and the presence of "EFI" means a total mess, a mix of Legacy and UEFI installations.
Start over. With UEFI it doesn't matter which OS you install first but before anything else boot a Ubuntu live session, open GParted and in the Device menu choose "New partition table" and select "GPT" (Note: This will delete everything). Now your drive is prepared to have proper UEFI installations of Windows and Ubuntu.

---

### Post by gabelumayog0509 on 2020-04-06
Is there anyway I can access my files in windows 10 through ubuntu since I don't want to lose my files before I format for a proper EUFI.

---

### Post by CelticWarrior on 2020-04-06
If the Windows partitions aren't encrypted and have no errors then yes, the files are accessible from a Ubuntu live session.

---

### Post by oldfred on 2020-04-06
Boot-Repair is really only for Linux repairs.
About the only Windows repair it does is restore an old BIOS bootloader to MBR. But with UEFI it cannot do much. 
You typically need a Windows repair/recovery flash drive for Windows repairs.

What brand/model system?
What video card/chip?
Many need UEFI update and if SSD, SSD firmware update to work with Linux.
And drives set to AHCI, not RAID nor Intel RST which prevents Linux from seeing drive.
And Windows fast start up must be off to see NTFS partitions.

---

### Post by gabelumayog0509 on 2020-04-06
I tried transferring files through ubuntu but It couldn't read my hdd. I found a solution online by editing the mount options by adding ro in, nosuid,nodev,nofail,x-gvfs-show,ro. After I edited the mount options it was able to read the information inside my hdd. However, when I tried to transfer files to my external hard drive. The files I transferred was not usable. Sometimes I can transfer some files to my external hdd, but it's not usable when I try to access it on a different laptop. Now, I am getting an error splicing file: Input/output error. How do I fix that error? Thanks.

---

### Post by gabelumayog0509 on 2020-04-06
Lenovo ideapad 320-15ABR
AMD A12-9720p Radeon r7, 12 compute cores 4c+8G

---

### Post by oldfred on 2020-04-06
This may not apply to your model, but often UEFI update required anyway.

UEFI update required for USB-C port issues 2017 thru 2019 models
ThinkPad models including the ThinkPad X1 Carbon (5th Gen to 7th Gen), X1 Yoga (2nd Gen to 4th Gen), and P-series 
[https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/](https://www.cnet.com/news/is-your-thinkpads-usb-c-port-not-working-upgrade-its-firmware/)

From Ubuntu & Disks application, the icon in upper right corner shows SmartStatus. That can run hard drive tests, but all I really know is if it says drive is good or bad. Check if drive is ok or not.

---

### Post by CelticWarrior on 2020-04-06
> The files I transferred was not usable. Sometimes I can transfer some  files to my external hdd, but it's not usable when I try to access it on  a different laptop. Now, I am getting an error splicing file:  Input/output error.

This means, unfortunately, that your HDD is either defective (worst case scenario) or has logical errors (best case scenario). Assuming the best case scenario you may try Windows tools to correct the errors and/or retrieve the files. Worst case scenario, the files are lost, replace the drive and reinstall.

---

### Post by gabelumayog0509 on 2020-04-06
I have 7k+ bad sectors and it says disk is ok. I was able to transfer one video but the quality is altered. So, its either my files are still there and I'm just getting errors because the reason for quality is I had to cancel the transfer of the file because it was taking too long for a small file or the file is altered because the hdd is dead. I'll just transfer my files when my sata to usb adapter arrives and see whether errors are causing my problems or bad 1tb hdd.

Thanks for the help you guys <3

---

### Post by TheFu on 2020-04-06
> 7k+ bad sectors 
That's a bunch of data loss.  i'd stop using that drive immediately.  The only thing it should be used for going forward to for read-only, attempts to get data off the drive.  Use ddrescue to clone each partition with data you want onto a completely new HDD.

BTW, don't try to fix Windows problems with Linux.  That used to be possible before UEFi and MSFT started using weird partition hacks to make the storage appear faster - so about the time Win8.0 was released.

---

