---
title: "asus a9rp vs. ubuntu 9.04 sound problem"
date: 2009-06-01
forum: Hardware
---

### Post by akosasus on 2009-06-01
Hi!

My realtek ac 97 soundcard works but the problem is that permanantly make some noise.

I found this solution:

 To solve audio and wireless problems, users follow the instructions bellow: 
   1-Download and install kernel sources, I copied it to /usr/src/ 
   2-Get this patch for audio and decompress to your kernel source root folder, say it is:/usr/src/linux-2.6.21-5 
  [ftp://ftp.alsa-project.org/pub/kernel-patches/alsa-git-2007-05-03.patch.gz](ftp://ftp.alsa-project.org/pub/kernel-patches/alsa-git-2007-05-03.patch.gz)   so, you should have alsa-git-2007-05-03.patch in your linux kernel source folder 
   3-Open console and run: 
  patch -p1 <alsa-git-2007-05-03.patch   OK, Now kernel is patched for audio, we proceed to wireless. 
   4-Say your kernel source folder is /usr/src/linux-2.6.21-5, open this file:
/usr/src/linux-2.6.21-5/drivers/net/wireless/zd_usb.c and add this line to the ZD1211-B section: 
 { USB_DEVICE(0x0b05, 0x171b), .driver_info = DEVICE_ZD1211B },    Save the file. 
  5-Now you should download this file and decompress the content into /lib/firmware/zd1211(if this directory does not exist, create it) 
 [http://sourceforge.net/project/showfiles.php?group_id=129083](http://sourceforge.net/project/showfiles.php?group_id=129083)   
OK,we are almost done!Now, you should compile the new kernel and install it.You can open /usr/src/linux-2.6.21-5/README.txt to find out how to do so. what I did: 
   cd /usr/src/linux-2.6.21-5
Make oldconfig
Make
Make modules_install
Make install 
   If using GRUB, you are done!Reboot and enjoy:)
If using LILO, reinstall LILO and reboot and enjoy! 
   The above procedures should work all of the linux distributions.

My question is: This solution works?
What means this: Download and install kernel sources, I copied it to /usr/src/?
Please help!
Thanks!

PS. I have also problems with stand by and hibernating.

---

