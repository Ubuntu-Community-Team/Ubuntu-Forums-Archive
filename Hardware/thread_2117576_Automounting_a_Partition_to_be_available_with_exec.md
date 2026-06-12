---
title: "Automounting a Partition to be available with exec permissions"
date: 2013-02-18
forum: Hardware
---

### Post by HexTonkLys on 2013-02-18
Hi,
I have installed ubuntu 12.10 64-bit into a 30gb partition, Windows 7 into a 60gb partition and have a 600gb ntfs data partition all on the same drive. Everything works just fine, Windows and Ubuntu access the data partition fine. 
However recently I installed the Steam game client and realised that it automatically downloads game files onto the Ubuntu Partition into its default files folder. So I specified a separate folder for the Steam files to be located but it gives an error saying ,
New Steam Library folder must have be specified toa filesystem with read write and execute permissions.

So, I found a solution [here]("http://askubuntu.com/questions/18052/exe-file-permission-fail/18053#18053") , which works. But I wanted to put this into my /etc/fstab so that I don't have to do it manually everytime I reboot. I have been looking through the man docs in terminal and have got to the point where the partition automounts but it does not automount with the exact parameters given in the link above. I was wondering what I would add to the /etc/fstab file to give the same parameters as those in the above solution???

Any help is greatly appreciated,
Regards

---

### Post by thermion on 2013-02-19
Just add your options to your /etc/fstab file like this:

/dev/...        /path/to/mountpoint/        [filsystemtype]        [option1,option2,option3]        0        0

Replace these values, so they may look something like this:

/dev/sdb1        /media/vista        ntfs        fmask=0022,dmask=0000,uid=1000,gid=1000        0        0

---

