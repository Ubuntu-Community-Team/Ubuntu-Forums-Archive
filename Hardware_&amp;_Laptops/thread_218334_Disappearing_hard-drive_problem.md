---
title: "Disappearing hard-drive problem"
date: 2006-07-18
forum: Hardware &amp; Laptops
---

### Post by pwaller on 2006-07-18
Note that I have already posted this on the laptop forum at [http://www.ubuntuforums.org/newthread.php?do=newthread&f=135](http://www.ubuntuforums.org/newthread.php?do=newthread&f=135) already, but I am posting it here because I'm not convinced this is a problem caused by the fact it is a laptop.

Here is what I have done so far:

I got a new laptop, completely fresh with nothing on it. I have the DVD version of the 6.06 install/livecd. It boots fine (though with a minute or two wait at the "Mounting root filesystems..." screen.

I then proceeded to partition and install linux, everything seems fine.

Restart, and after waiting at the "Mounting root filesystems..." screen for quite a while (5 min+) I get "Alert! /dev/sda1 does not exist. Dropping to a shell". It then gives me a shell in which I can't seem to do anything.

Rebooting back into the livecd, /dev/sda1 (the root partition) and /dev/sda5 indeed don't exist. However, they are listed under fdisk -l, and displayed in gparted. However I can't seem to access them for love nor money.

Deleting the partition, and creating a new one - I can mount it, and write files to it happily. If I reboot back into the livecd, it disappears, and I haven't yet found any way of accessing it.

complete dumps of dmesg and lspci -v can be found at [http://misc.randomphp.net/dmesgdat](http://misc.randomphp.net/dmesgdat) and [http://misc.randomphp.net/lspcidat](http://misc.randomphp.net/lspcidat)

Any help is greatly appreciated. I currently don't have a functioning computer to work on! :(

Thanks in advance for any help. 

- Pete

---

