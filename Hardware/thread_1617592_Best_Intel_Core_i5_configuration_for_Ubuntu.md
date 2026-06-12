---
title: "Best Intel Core i5 configuration for Ubuntu"
date: 2010-11-09
forum: Hardware
---

### Post by arbos on 2010-11-09
Hello. I want to run Ubuntu 10.10 on this following system:
Gigabyte H57M-USB3
Intel® CoreTM i5-760 2.8GHz, 8MB
1) It's work on Ubuntu ?
2) What is the best i5 configuration for Ubuntu ?
Thank you.

---

### Post by ajgreeny on 2010-11-09
It should work without problem I think, but what do you mean by configuration?

If you are asking about the best partition setup you may get many different answers, but the one likely similar point from everybody will be to have a separate root partition (/ as ext4) and home partition (/home, also ext4), which you can set up at install time most easily.  Make the root partition about 10GB, and home can be the rest, except for a swap partition of probably about 4GB.

If you are dual booting with Windows you may feel it's appropriate to make a shared /data partition, formatted as ntfs so both OSs can read and write to it, in which case the /home partition will not need to be very big as it will only contain configuration files and folders, but none of your data (docs, pictures, music, videos, etc etc).  To get the data partition mounted at boot will require either an easy edit of /etc/fstab, or the use of the various ntfs file management packages in ubuntu, none of which I can help with as I have no Windows to deal with any more.

---

