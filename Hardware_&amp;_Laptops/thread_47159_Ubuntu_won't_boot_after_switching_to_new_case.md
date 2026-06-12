---
title: "Ubuntu won't boot after switching to new case"
date: 2005-07-07
forum: Hardware &amp; Laptops
---

### Post by mcduck on 2005-07-07
I finaly got today new case for my computer. After moving all hardware from old case to new one I of course tried to boot into Ubuntu. But life isn't that nice, as i soon got to realise :(

Everything seems to work nicely, except that after line "Starting Ubuntu" I get this:
```
pivot_root: No sush file or directory
/sbin/init: 428: cannot open dev/console: No such file
Kernel panic - not syncing: Attempted to kill init!
```
..and then nothing. Honestly, this error text doesn't help me a bit. 

Sure, I checked that all is properly connected. Even my Win2K insatallation from the very same hard drive works ok. Only change to old setup is, that I left out an old CR-RW drive, but surely THAT can't be such a serious problem to linux?

What could be wrong, and how can I get my Ubuntu working again? If somebody knows what that error message is trying to say, please help!

edit: You propably want to know about my setup: I got a Samsung IDE-disk as primary IDE master, at second IDE channel I only got a CD-RW/DVD-drive, and then there is a SATA-HD connected to motherboards SATA-RAID-controller. Linux and Win are both installed to IDE-disk. In old setup I also had a second CD-drive in second IDE-channel.

---

### Post by intangible on 2005-07-07
Have you installed any packages from breezy?

---

### Post by mcduck on 2005-07-07
oh, it seems that in my previous setup harddisks were for some reason installed to secondary IDE, and optical medias to primary one. Connecting them now to correct channels wasn't a broblem for grub or windows, but linux didn't like it. :P I switched cables and now everything works again. I suppose I just have to keep the cables in wrong channels from now on..

Sorry about making this thread so quickly, I should have spent a bit more time with google as it helped me quickly find out that this error had something to do with harddisks/partitions. After that the rest was about trying all possible combinations with IDE-cables until Ubuntu booted again. 

(It seems that people get confusingly matching errors with kernel updates. Luckily that wasn't the problem :) )

---

### Post by intangible on 2005-07-07
The two files you'll need to update to match the new setup would be **/etc/fstab** and **/boot/grub/menu.lst**, just be sure to have a live cd handy to fix it if you get it wrong :D

---

### Post by mcduck on 2005-07-07
thanks, If those files are all that need editing, I'll backup my current files and try to make everything work with cables connected in right IDE-channels. 

After hours of twisting single wires to motherboard pins to connect everything I was sure I had connected something wrong, and even if there was no smoke the kernel panic made me panic ;) (damn those too short cables and usb- and firewire connectors divided to single wires :D )

---

### Post by intangible on 2005-07-07
If you want to post those config files here, and describe your new setup, I will see if I can get you the correct setup.

---

### Post by mcduck on 2005-07-08
Thanks for offering help, but I guess i'll learn a lot more if I'll try to figure it out myself.. :)

---

