---
title: "Can't change SATA mode from optane"
date: 2019-12-07
forum: Hardware
---

### Post by clllv1 on 2019-12-07
I bought a laptop which has this ssd [https://www.westerndigital.com/products/internal-drives/pc-sn520-ssd](https://www.westerndigital.com/products/internal-drives/pc-sn520-ssd)
bios sata mode is set to Optane without raid, and Ubuntu installer doesn't detect the ssd. I've searched in Google and you have to change the mode in BIOS but i cant do so. I've also read that you can change it in windows 10 but I didn't really understand how, could someone help me? Thanks in advance.

---

### Post by oldfred on 2019-12-07
The mode you want is AHCI, and if dual booting with Windows you must first install the AHCI drivers into Windows.

Often issue is that you need UEFI update and SSD firmware update, even if new hardware. Check that you have latest versions of firmware.

What brand/model system?
 Someone posted one brand required a shift & some key to get choice of AHCI to appear. 
Some also require you to set an UEFI password (never forget that or reset when done).
Check your system manual for UEFI/BIOS settings & how to change them.

---

### Post by clllv1 on 2019-12-07
Laptop is new, I was going to install Ubuntu, not dual boot.
Model Acer Aspire 3 A315-54K-59NZ
[https://www.acer.com/ac/es/ES/content/model/NX.HM2EB.005](https://www.acer.com/ac/es/ES/content/model/NX.HM2EB.005)

So basically I can install windows (already downloading it), download AHCI drivers, then change it in BIOS (won't be locked anymore) and then installer Wil detect it?
How do I check firmware versions?
Edit: sorry for spanish link but I didn't find the exact model in English acer page.

---

### Post by oldfred on 2019-12-07
Acer is one with some unique requirements, but most models seem to work well.
One requirement is that after install you have to enable "trust". It seems to only trust a Windows boot entry by description "Windows Boot Manager". But you can add trust to other installs.

Be sure to boot in UEFI boot mode. Both Windows & Ubuntu installers, will install in the same mode as you boot install media.

Issues by brand are often common as same UEFI used with just minor changes for hardware differences. Bigger difference if Intel or AMD. So other Intel Acer may have same issues.

       Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    
Acer has just started better support for Linux. Probably not as good for older systems.
       Acer Begins Publishing UEFI Firmware Updates For Linux Users On LVFS For Fwupd,  Aspire A315 laptop first
[https://www.phoronix.com/scan.php?page=news_item&px=Acer-Updates-On-LVFS](https://www.phoronix.com/scan.php?page=news_item&px=Acer-Updates-On-LVFS) 
    
       Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)

---

### Post by clllv1 on 2019-12-07
I'm afraid I don't understand your post, sorry. I have a new laptop and Ubuntu installer doesn't detect SSD (windows did perfectly) due to Intel optane. I can't disable it in BIOS, is there other way to do it? I don't want to dual boot, only Ubuntu.
Thanks for taking the time to help me with all those links, but I think I didn't explain my situation well in first post.

---

### Post by oldfred on 2019-12-07
Intel Optane - See Intel response that no performance difference between RAID & AHCI.
[https://communities.intel.com/thread/121155](https://communities.intel.com/thread/121155)

While HP, similar issue.
[https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved](https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved)

I thought it was an Acer where the user has to use control-something to get the menu to open up to change to AHCI.
       
 Acer Nitro 7 Missing AHCI mode Ctrl + S in UEFI
[https://ubuntuforums.org/showthread.php?t=2429951&p=13900969#post13900969](https://ubuntuforums.org/showthread.php?t=2429951&p=13900969#post13900969)

---

### Post by clllv1 on 2019-12-07
Sadly I don't think we are understanding each other. I just want to change sata mode to AHCI, I tried ctlr s in bios but didn't work.
Again thanks for your effort, I appreciate it.

---

### Post by oldfred on 2019-12-07
If you have updated UEFI, have UEFI Secure boot on with your own password and your manual says to use contol-S like previous post, I would ask on the Acer site/forum.

---

