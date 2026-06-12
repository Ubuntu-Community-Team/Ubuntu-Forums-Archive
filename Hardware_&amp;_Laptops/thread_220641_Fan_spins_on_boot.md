---
title: "Fan spins on boot"
date: 2006-07-21
forum: Hardware &amp; Laptops
---

### Post by irober02 on 2006-07-21
I have a new Dell Inspiron 6400 on which I have installed Dapper. Everything's working beautifully (wifi + WPA, graphics, sound...). A problem I do have is at boot up. Sometimes (often?) when it boots, just after the kernel starts, a fan starts spinning and keeps spinning. In this state, the system runs very slowly -I've never bothered to wait for it to finish booting. I throw the dice again (hit the power button) and eventually it starts up OK. It seems that when all goes well, the fan spins up briefly (<1 sec) and then stops and the machine then boots properly.

I have:
Intel Dual Core T2500 @ 2.0GHz
Linux 2.6.15-26-686 #1 SMP PREEMPT 

I've not been able to dig out any obviously helpful entries in the logs.

---

### Post by irober02 on 2006-07-31
Further information: By pausing the boot process on the grub menu I have determined that this fan problem seems to be grub-related as no OS/kernel has yet started. This seems to be the same problem as reported by Paul ([http://ubuntuforums.org/showthread.php?t=225711&highlight=fan+boot](http://ubuntuforums.org/showthread.php?t=225711&highlight=fan+boot)) -although Phe's reporting it for a desktop.

---

### Post by frankuzzo on 2006-07-31
> **irober02 said:**
> ([http://ubuntuforums.org/showthread.php?t=225711&highlight=fan+boot](http://ubuntuforums.org/showthread.php?t=225711&highlight=fan+boot))  I replayed tere, maybe it was more laptop related topic. Anyway we can continue the discussion here or there as you wish. 

Ciao.

---

### Post by irober02 on 2006-08-02
Over the last couple of days I've received a large number of (k)ubuntu updates. I think there was a a grub update amongst them. Since last night, I've booted about 6 times without a single fan problem. :) I'm keeping my fingers crossed that perhaps some clever people have fixed the problem. How is your fan going?

---

### Post by irober02 on 2006-08-06
I spoke too soon. I still have the problem of the fan spinning fast and the computer crawling slowly on some bootups. :-(

---

