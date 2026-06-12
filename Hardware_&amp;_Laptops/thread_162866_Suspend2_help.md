---
title: "Suspend2 help"
date: 2006-04-19
forum: Hardware &amp; Laptops
---

### Post by jhk on 2006-04-19
Hi, I'm trying to get suspend2 to work on my new HP DV1000 laptop.  I've compiled it in to the kernel and it seems to shut down fine without any errors, however when I turn it on again it just goes through the usual grub selection and bootup, with no sign whatever  that it was in hibernation.  I know that you are supposed to append a suspend2 option to your kernel line in Grub's menu.lst and then re-install Grub,  and I think I've done it properly- I've tried both the ram (suspend2=swap:/dev/sda7) and disk (resume2=file:/dev/sda6:0xc1210) suspends but the computer still acts the same.  

Can anyone help?  Thanks!!

---

### Post by Griffin3 on 2006-04-20
See [http://ubuntuforums.org/showthread.php?t=75443&highlight=suspend2](http://ubuntuforums.org/showthread.php?t=75443&highlight=suspend2)

---

### Post by jhk on 2006-04-20
Thanks for the link... But the resulting kernel wouldnt boot up properly (it doesn't seem to see my sda drive, even though I've compiled the proper kernel drivers) so I'm trying the debian package commands from this thread to see if that works... 
[http://ubuntuforums.org/showthread.php?t=150864](http://ubuntuforums.org/showthread.php?t=150864)

---

### Post by jhk on 2006-04-21
Okay, I tried that method and it still does the same thing.  Is it because my drives are SATA instead of ATA???

---

### Post by Griffin3 on 2006-04-24
Very, very likely.  You need to make sure the SATA drivers are compiled into the kernel, not compiled as modules.  It should be somewhere in the make menuconfig step ...

---

