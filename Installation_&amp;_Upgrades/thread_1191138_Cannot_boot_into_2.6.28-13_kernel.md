---
title: "Cannot boot into 2.6.28-13 kernel"
date: 2009-06-18
forum: Installation &amp; Upgrades
---

### Post by lethalfang on 2009-06-18
I upgraded to 2.6.28-13 on my laptop (Gateway M-6862 with ATI Graphics), and after that I cannot boot into my desktop. After the "status bar" completes in the boot-up screen, it goes to a blank screen with some ubuntu logo on it, but it gets stuck there. 
It's the amd64 version with ext4 file system. 
Booting into the 2.6.28-11 option in GRUB is fine, but it does not boot into the 2.6.28-13 option. 

What's wrong???

---

### Post by lethalfang on 2009-06-18
Anyone got any ideas to fix this?

Thanks in advance.

---

### Post by Amilo1718 on 2009-06-18
i'll do a reboot into 2.6.28-13 soon ;)

---

### Post by lethalfang on 2009-06-18
After seeing [this post]("http://ubuntuforums.org/showthread.php?t=1191087#2"), I fixed the problem by un-installing ATI Catalyst 9.5 driver, then installed the 9.6 version [which just came out several days ago]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.2&lang=English").

---

