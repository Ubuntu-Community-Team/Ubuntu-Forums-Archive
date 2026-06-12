---
title: "[SOLVED] can't remove ubuntu completely under vista"
date: 2008-09-21
forum: General Help
---

### Post by krezol on 2008-09-21
I have used the Wubi installer in Vista x64 Home Premium. when I had a problem with Ubuntu 8.04 I used the Wubi uninstaller that was listed under Remove Programs in Control Panel. All the files that Wubi put on the Windows partition were removed but I still have Ubuntu listed as the other OS when I boot my computer. I used EasyBCD but it doesn't show me Ubuntu, only Vista as an OS to select. How do I remove Ubuntu completely?

---

### Post by xj0hnx on 2008-09-21
That's odd, I used EasyBCD to clean up mine too, I had four entries from trying it over, and over. I could never get it to run like that, I had to install Ubuntu on a different disc.

---

### Post by masterwillems on 2008-09-22
If you go to the windows logo (start) and then type msconfig at search, go to startup computer (second tab from the left) and you will see the different operating systems that can boot on startup, select ubuntu and click on remove.

If im correct, then you wont have the ubuntu option when the computer starts.

---

### Post by krezol on 2008-09-22
> **masterwillems said:**
> If you go to the windows logo (start) and then type msconfig at search, go to startup computer (second tab from the left) and you will see the different operating systems that can boot on startup, select ubuntu and click on remove.

If im correct, then you wont have the ubuntu option when the computer starts.
sorry, msconfig does not see the Ubuntu. Each time I install Ubuntu and then uninstall it using Wubi, I see another Ubuntu entry for the OSs to boot to. I am using brand new HP Pavilion dv9000 laptop.

---

### Post by ago on 2008-09-22
It's quite strange that you cannot see an entry using EasyBCD and the windows system configuration app. Do you have any non standard boot mechanism? Do you use ntldr(XP) as main bootloader?

---

### Post by masterwillems on 2008-09-23
Quote from a other topic:

> **dodle said:**
> You should be able to just delete the files under C:\.  There should be a folder named 'ubuntu', a file called 'wubildr', and one called 'wubildr.mbr', then delete the ubuntu entry in the Windows bootloader.

try that.

---

### Post by ago on 2008-09-23
It is a known issue of rev 505 to have uninstallation problems (see [https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu](https://wiki.ubuntu.com/WubiGuide#Cannot%20uninstall%20Ubuntu) an uninstaller is attached) but what krezol mentions seems to be a different matter.

---

### Post by masterwillems on 2008-09-26
I have the same issue now(but then regarding Wubi 8.10 Alpha), I removed everything that has to do with ubuntu (so the map ubuntu on the C:\ drive and every file that is in it (and to be shure i put it trough a shredder)) and also removed every register file that has something to do with ubuntu. And still it comes up with the Ubuntu option when i boot.
I also tried [THIS](http://www.vistabootpro.org/) program but that did not see the ubuntu boot file.

Someone said that there was a Boot.CFG file somewhere in Windows (probably in the C:\Windows folder, I only found a BOOTCFG.exe but that isnt changeble since it is a execute file and not a .CFG file.)

---

### Post by originalsurfmex on 2008-10-04
i am having the same problem using vista home premium (hp pavilion tx 2000).  in addition to not being able to remove my wubi installs (8.04 and 8.10 beta), even though i have uninstalled both wubi installs, when i select on of the 2 ubuntu boot options, ubuntu begins to boot up...which it shouldnt if it had gotten uninstalled in the first place.  ubuntu however never finishes booting up - its as if it was never completely removed even as an operating system.

---

### Post by ago on 2008-10-06
You can follow the manual uninstallation procedure.
[https://wiki.ubuntu.com/WubiGuide#Uninstallation](https://wiki.ubuntu.com/WubiGuide#Uninstallation)

---

### Post by originalsurfmex on 2008-10-07
thank you very much for the guide.  easybcd did the trick!

---

