---
title: "Kernel Alert /dev/hdb1 not found"
date: 2005-12-11
forum: Hardware &amp; Laptops
---

### Post by sitara on 2005-12-11
I have built an Ubuntu server system on a hard drive on one machine and installed the hard drive on another machine. After loading the kernel, the following message appears: 'ALERT /dev/hdb1 does not exist dropping to a shell'.

Can someone please explain what is going on and how to fix it?

Thanks in advance.

Keith

---

### Post by Lambert on 2005-12-11
On the machine you installed, was there a second drive on that machine? 

What it sounds like to me is your fstab has an entry for a second harddrive and when loading it doesn't see that hard drive any more.

you need to look at your file /etc/fstab and remove  the entry for hdb1 and any other modifications that look like it needs to accomodate the new box.

---

### Post by sitara on 2005-12-11
Thanks for the suggestion. Yes, there was another drive installed in the machine on which I built the system, but I disconnected it when I booted of this new disk. The strange thing is, if I put the new drive back in the original system, it boots fine. 

Anyway, the fstab was pointing to /dev/hdb, so I changed it to the following, but still get the same result. 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1

I also changed /boot/grub/device.map to look like this :

(hd0)	/dev/hda

although it seems like we got past that stage.

I still get the same result. Is there some other place that the device address is stored? 

I saw another thread about a similar message with the new kernel 2.6.15. I ran an apt-get dist-upgrade on my system this morning, but as far as I can see it's still running 2.6.12.

Any other suggestions would be welcome.

Keith

---

