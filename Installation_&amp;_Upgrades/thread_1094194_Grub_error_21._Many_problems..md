---
title: "Grub error 21. Many problems."
date: 2009-03-12
forum: Installation &amp; Upgrades
---

### Post by Kirbyray on 2009-03-12
First time Ubuntu user. Was using Windows XP, unfortunately I fell victim to some viruses and spyware. I used a Ubuntu 8.10 (Intrepid Ibex) boot disc. I installed ubuntu on my internal SATA hard drive and when installing I installed using the whole hard drive effectively reformatting it wiping it of any problems. When restarting and trying to boot ubuntu from the hard drive I encounter a GRUB error 21. I've read up and attempted to fix it by using terminal VIA;

sudo grub
root (hd0,0)
setup(hd0,0)

and it says it's worked but when restarting the same error occurs. I've also learned that you cannot restart the computer otherwise during startup it will shut down after 20 seconds of it being turned on.

I've also looked at my BIOS setup and it can't detect any primary slave (which to me (someone computer illiterate) seems to me that it doesn't see the hard drive).

I've also attempted to alter the boot/grub/menu.lst but I don't think I know what I was doing very well.

My last attempt may be to burn Windows Vista on a disc (and maybe a recovery disc if it may help) any attempt to install it on my internal hard drive but if it's the BIOS that's the real problem it wouldn't work anyway would it?

Any help would be appriciated.

---

### Post by Neo_The_User on 2009-03-12
Can you boot into Ubuntu at all from HDD? If so, I can help. If not, I can't.

---

### Post by dstew on 2009-03-12
Do you get any message with the error, or does it just say Error 21 and quit? If you just get the error, then it is probable that grub is mis-installed, such that the stage1 file in the MBR of the boot disk cannot find or mount the stage2 file, which might be on your SATA. I assume you have two disks in there.

Anyway, to get it working, you will need to re-install grub. You seem to have tried this. Did you follow [this How-To]("http://ubuntuforums.org/showthread.php?t=224351"), and use the **find** command first?

EDIT: I note that your grub installation commands may be wrong. If **find /boot/grub/stage2** yielded (hd0,0), that means your **root** should be (hd0,0), but your **setup** should be (hd0) or (hd1), depending on which disk your BIOS boots. Setup (hd0,0) will install grub stage1 into the first ***partition*** of disk 0, and not in the ***MBR*** of disk 0. You may have a mis-directed grub in the MBR that your re-installation commands are not correcting, hence the error repeats.

---

