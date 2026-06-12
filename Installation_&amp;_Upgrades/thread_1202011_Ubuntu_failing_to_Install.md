---
title: "Ubuntu failing to Install"
date: 2009-07-01
forum: Installation &amp; Upgrades
---

### Post by HerroRygar on 2009-07-01
Hi,
 
I'm trying to install 9.04 from a cd. I verified the hash of the ISO file, I burned the cd, and verified the contents of the cd using the boot menu. In fact, I USED to be able to boot into Ubuntu and, had I wanted to, select the install option from there.
 
...but I JUST today put in a new, bigger harddrive...and partitioned it, placing the Windows 7 release candidate in the first partition. Now, when I try to either install Ubuntu or boot without installing, I get the Ubuntu loading screen...which completely freezes after a few seconds. I can verify the files on the cd all I want, but it just won't load. Any thoughts? Is there some reason why the Windows kernel would be interfering, or perhaps the way I've partitioned this drive?

---

### Post by redorchestra on 2009-07-01
I am having the same problem.
I am cobbling together a new/old machine.
I put my two old drives on a new motherboard. 
I thought my dualboot would power up the same as usual.
I didn't realize that OSs were processor dependant ;p.
Anyway to make a long story shorter.
I have all my drives recognised. I used the live cd to install 9.04 running with xp service pack 2.
I upgraded to service pack 3, and now ubuntu won't load.
I tried a reinstall but I get to pick the language, try to install and I get the cylon scanner for about 2 minutes. then a blank screen, then a list of errors about usbs and bad logic sectors.
 
From windows I can acess the livedisk, and I installed inside windows. This seems to work pretty well. 
 
Can you install inside windows?
Does that slow down Ubuntu?
It seems to me that it just eliminates the Grub loader.

---

### Post by raymondh on 2009-07-01
> **HerroRygar said:**
> Hi,
 
I'm trying to install 9.04 from a cd. I verified the hash of the ISO file, I burned the cd, and verified the contents of the cd using the boot menu. In fact, I USED to be able to boot into Ubuntu and, had I wanted to, select the install option from there.
 
...but I JUST today put in a new, bigger harddrive...and partitioned it, placing the Windows 7 release candidate in the first partition. Now, when I try to either install Ubuntu or boot without installing, I get the Ubuntu loading screen...which completely freezes after a few seconds. I can verify the files on the cd all I want, but it just won't load. Any thoughts? Is there some reason why the Windows kernel would be interfering, or perhaps the way I've partitioned this drive?

I have an older machine/BIOS (vintage '98) which I installed a newer, bigger HD.  I had problems installing.  I learned that on older BIOS', there is a cylinder limit and that I needed to install Ubuntu within the first 8GB of the drive.

I see no reason why windows would interfere.  I have win7 dual-booted as well.

How did you partition?  Also, can you share your system specs?

---

