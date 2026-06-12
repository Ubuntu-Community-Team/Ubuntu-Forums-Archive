---
title: "LBA64 support for Areca ARC-1220 SATA RAID card"
date: 2007-01-04
forum: Hardware &amp; Laptops
---

### Post by chipeast on 2007-01-04
A cross post from general, seen here:

[http://ubuntuforums.org/showthread.php?t=331683](http://ubuntuforums.org/showthread.php?t=331683)

*******************************

Friends:

Looking for your help on this....

I just installed an Areca ARC-1220 SATA RAID card in a new machine (Intel D975Xbx2 board with 2.4gh Core2Duo with Ubuntu 6.10 desktop). It has five 750gb drives in RAID5 attached for an archive (and a 320gb for boot). Since the final size is 3TB, according to the enclosed docs, I need to do this:

__________________________________________

Using greater than 2TB volume in Linux by “LBA 64” option 

Notice : Please make sure that your system have ‘Large Block Device’ support enabled. 
To enable it, open a Terminal Command console, then type : 
# cd /usr/src/linux2.6 
# make menuconfig 
A configuration menu will open on the screen. Select ‘Device Drivers’ > ‘Block Devices’. There 
has a item called ‘Large Block Device’. Put an * on it. Save and exit. Then type : 
# make 
# make modules 
# make modules_install 
# install 
When it is all done, reboot system. You will find a new option for custom kernel in menu. Boot from this new kernel. 
_________________________________________

but on the second command, I never get a config menu.... just a return to $.

So..... two questions:

1) According to several references, the driver was added to 6.10.... Gparted sees the device as /dev/sdb but only lists 745.97GB.... so does the driver work, or is Gparted just smart? And what additional driver suggestions can you please make?

2) After viewing the above LBA64 suggestions to handle partitions larger than 2TB, can you please suggest where the instructions need to be modified for Ubuntu?

MANY thanks for your help.......... Chip

---

