---
title: "Grub corrupted on update?"
date: 2009-08-19
forum: Installation &amp; Upgrades
---

### Post by opto09 on 2009-08-19
Hi all. I'm having a funny problem with updates on the linux headers. It seems everytime I update it, grub's menu.lst gets overwritten and the root location gets changed to a funny string of numbers which means that grub returns an Invalid Device string. This seems to happen only when I update the kernels(?) like I did this morning. Any ideas how to fix this and stop it from happening again?

---

### Post by stlsaint on 2009-08-19
can you post exactly what error you are getting? i too have kernel problems and we may be able to assist one another!

---

### Post by opto09 on 2009-09-06
It's not a kernel error per se. It's just that Grub's menu.lst points to the wrong root and cannot retrieve the kernel. The error I get is something like "error location not valid".

---

### Post by presence1960 on 2009-09-06
> **opto09 said:**
> Hi all. I'm having a funny problem with updates on the linux headers. It seems everytime I update it, grub's menu.lst gets overwritten and the root location gets changed to a funny string of numbers which means that grub returns an Invalid Device string. This seems to happen only when I update the kernels(?) like I did this morning. Any ideas how to fix this and stop it from happening again?

did you get to 9.04 via a dist upgrade? If so I have seen quite a few dist upgrades which have left the root (hdx,y) format inplace. Unfortunately 9.04 uses that long string of numbers which are the UUID to identify partitions. I will post an example of my menu.lst so you can see.

```
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-15-generic
uuid		958bcb08-eb90-435a-a1b5-ddc12d0727f4
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-15-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid		958bcb08-eb90-435a-a1b5-ddc12d0727f4
kernel		/boot/vmlinuz-2.6.28-15-generic root=UUID=958bcb08-eb90-435a-a1b5-ddc12d0727f4 ro  single
initrd		/boot/initrd.img-2.6.28-15-generic
```

Unfortunately your GRUB is the problem, the kernel updates are only doing what they are supposed to do in 9.04, which is use UUID instead of root (hdx,y)

I would try this, go to Synaptic package manager and select grub for complete removal. Do not choose mark for removal because it will reinstall whatever package is cached when you install it again. Complete removal will remove GRUB and the cached package. Click apply. When complete go back to grub in synaptic and mark it for installation. This should install the proper version of GRUB for 9.04. Do not reboot until both complete removal and install are done or you will not be able to boot your machine. For good measure i would open a terminal and run > sudo update-grub

---

### Post by opto09 on 2009-11-10
> **presence1960 said:**
> 
I would try this, go to Synaptic package manager and select grub for complete removal. Do not choose mark for removal because it will reinstall whatever package is cached when you install it again. Complete removal will remove GRUB and the cached package. Click apply. When complete go back to grub in synaptic and mark it for installation. This should install the proper version of GRUB for 9.04. Do not reboot until both complete removal and install are done or you will not be able to boot your machine.

Yes that's kind of what mine looks like but it seems to not be able to find the root address. I'll have a go at reinstalling GRUB and seeing what happens.

---

### Post by presence1960 on 2009-11-10
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script 0.32 to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by opto09 on 2010-01-25
Hi sorry for the slow update. The problem is now solved by proxy of having done a fresh install. The problem I think is due to grub (possibly a menu.lst thing) not being configured or installed properly. I could fix the problem in the old installation by replacing
```
root XXXX-XXX-XX-XX-XX
```
with
```
uuid XXXX-XXX-XX-XX-XX
```

However the whole thing broke down when I tried a dist-upgrade to Karmic and to cut a long story short I ended up reformatting and reinstalling Ubuntu. The new grub2 installation no longer has this problem. Thanks everyone who replied.

---

