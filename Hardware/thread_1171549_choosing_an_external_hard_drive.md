---
title: "choosing an external hard drive"
date: 2009-05-27
forum: Hardware
---

### Post by mystmaiden on 2009-05-27
I'm needing an external hard drive to stash all my Poser stuff in, but I'm functioning pretty much in ignorance here. I'm looking to get one with a terrabyte of disk space but some do list as being compatible with Windows Vista or Mac and some do not list the compatibility at all -  haven't seen anything listed as compatible with Linux or Ubuntu specifically.  I'm on a budget so can't afford to get the wrong thing first.  Can I just buy whatever I find I like and nuke it and install Ubuntu or do I need to buy a certain type. Is there a brand that works consistently?

Any insight  would be helpful at this point.

Thanks! 
mystmaiden

---

### Post by mystmaiden on 2009-05-28
oh, and storage is pretty much all I'll need this for, if that makes any difference,

thanks
myst

---

### Post by mystmaiden on 2009-06-24
I asked around and searched around on the web and the consistent answer I got was that any external hard drive would work. I ordered a simpletech 1TB external and it came yesterday but now I have a problem. It is set up for NTFS. it gives an option for using with MAC but I'm really not sure what I'm doing here. 

When I plugged it in I got this error: 

Unable to mount volume  failed to mount '/dev/sdb1' operation not supported because NTFS is marked to be in use. Choose 1 option: If you have Windows then disconnect the external devices by clicking on safely remove hardware icon in the windows taskbar, then shut down windows cleanly. 

Choice 2:If you don't have Windows you can use the 'force' option for you own responsibility. For example type on the command line mount -t ntfs-3g/dev/sdb1/media/FV-U35 -0 force Or add the option to the relevant row in the /etc/fstab file 
/dev/sdb1/media/FV-U35 ntfs-3g force 0 0

My question is - am I going to be able to use this drive with linux? Is there something I can do to make it work. I'm running ubuntu 8.10 LTS which I installed in the default manner, with no changes. I have been on hold on simpletechs tech support for two hours now. 

I finally got the tech and he says that Mac (I am assuming the Mac installation instructions?) will allow me to set it up as FAT32, beyond that of course they would tell me nothing about whether or not it would work with linux.

Thanks!!
mystmaiden

---

