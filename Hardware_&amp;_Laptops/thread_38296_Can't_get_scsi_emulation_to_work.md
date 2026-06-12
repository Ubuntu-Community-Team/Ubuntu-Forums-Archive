---
title: "Can't get scsi emulation to work"
date: 2005-05-30
forum: Hardware &amp; Laptops
---

### Post by jonrkc on 2005-05-30
I followed instructions for enabling scsi emulation given in the wiki, but my device will not be recognized.  The step in the instructions telling me to check the /dev directory where I should find scdx devices listed, led me to at least one thing that's wrong.  The scd devices, including scd0 which should be my CD/DVD writer, appear in the .dev (dot-dev) directory, but not in the working dev directory (without the dot).  Linking from dev to .dev for the device didn't work--though it did for one other poster here:

[http://ubuntuforums.org/showthread.php?t=22545&highlight=.dev](http://ubuntuforums.org/showthread.php?t=22545&highlight=.dev)

I'm at a loss to know how to continue.  CD burning doesn't work right without recognition of the burner as a scsi emulating one.  Doing lsmod shows all the scsi modules in place in the kernel.  The fstab mounts the machine as scd0, supposedly.  But k3b won't recognize it except as an ATAPI device, and xcdroast, though it for some reason DOES recognize it as scsi enabled, won't work correctly with it, terminating with an inconclusive error message and a request to email the author of cdrecord.

Can anybody help me with this?

(One thing that really puzzles me is that kernel 2.6.x was supposed to do away with the need for scsi emulation.  When I used 2.6 with Mandrake/Mandriva, my device was recognized as scsi enabled without any intervention, during installation.  Why is this kernel 2.6 acting like 2.4 did, requiring the user to manually set up scsi emulation?)

---

### Post by jonrkc on 2005-05-30
OK: I found a typing error (I wrote scsi-ide instead of ide-scsi in the menu.lst file when I was redoing things during my troubleshooting).  I fixed that and now scd0 shows up in the /dev directory where it belongs, and xcdroast recognizes the drive but cannot finish writing to it (in this case blanking a CD-RW); k3b does not even see the device, and specifying it as /dev/scd0 brings k3b's response that there is no device there.  In Midnight Commander I get the information on the file listing that there is no such device.  

Attempting to mount the device to read a CD on it gets: Not a valid block device.  

So I'm pretty much where I was.   At this point I can't use my drive unless I want to go back to having it be simply ATAPI in which case I can read from it OK but writing is iffy at best.

---

### Post by jonrkc on 2005-05-31
Sorry to be monopolizing my own thread, but here's what I learned through a lot of Google searching, which more or less solved my problem.  (I've spent nine hours today trying to get CD burning to work; it worked when I first tried it under Ubuntu, and then it failed, why I don't know.)

I read a very clear exposition of how to enable scsi emulation.  In it, the writer said to examine /var/log/dmesg to make sure emulation was actually enabled.  I did that, and in the process found a message there stating that scsi emulation is deprecated now, and that you should use ide-cd instead of ide-scsi, and use it with /dev/hdx (where x is whatever letter goes along with your CD writer).  

So I changed all the entries in my /boot/grub/menu.lst from hdc=ide-scsi to /dev/hdc=ide-cd and rebooted.  Result: I was able to burn successfuly with xcdroast, though k3b still has problems.  It seems ATAPI burning is the preferred way now with the 2.6 kernels.  Xcdroast grumbles mightily about it, but works just as fast and well as with scsi emulation.  I think the burning programs haven't caught up to the kernel yet.  

Hope this may help somebody.  It's great if you can get emulation to work--and the wiki article here is very clearly and helpfully written.  But it might be worth trying ide-cd in case you run into trouble with scsi emulation.

---

