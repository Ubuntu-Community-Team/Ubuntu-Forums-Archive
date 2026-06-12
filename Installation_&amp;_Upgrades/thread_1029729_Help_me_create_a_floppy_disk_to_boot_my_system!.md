---
title: "Help me create a floppy disk to boot my system!"
date: 2009-01-03
forum: Installation &amp; Upgrades
---

### Post by Anaphylaxis on 2009-01-03
I was adviced on linuxforums.org to create a floppy with smart boot manager on it, but the #"!¤ thing won't compile properly. 

My computer won't boot from a live CD, nor from the hard drive itself, on which I have installed linux from another pc. I thought that, by putting linux + grub on the drive, the BIOS would fire up my new linux installation, but obviously, that ain't the case. 

Now, my pc only gives me the following feedback: 
Invalid boot diskette.
Insert boot diskette in A:

So, can anyone here help me create a boot diskette? Pretty please with sugar on top? :P

---

### Post by logos34 on 2009-01-03
you tried copying sbm.bin from the ubuntu install cd to the floppy like this:

cd /path/to/ubuntucd/install/

dd if=sbm.bin of=/dev/fd0

?

---

### Post by Anaphylaxis on 2009-01-03
No. Is there anything more I need to do than to copy that file to a floppy?

Will that file only start ubuntu, or can I start xubuntu or another distro with it?

---

### Post by logos34 on 2009-01-03
no, it's OS independant
[http://linux.simple.be/tools/sbm](http://linux.simple.be/tools/sbm)
[https://help.ubuntu.com/community/SmartBootManager](https://help.ubuntu.com/community/SmartBootManager)

login as root:

# mke2fs /dev/fd0
# cd /path/to/ubuntucd/install
# dd if=sbm.bin of=/dev/fd0
# cmp sbm.bin /dev/fd0

hope it allows you to boot the cd drive

---

### Post by Anaphylaxis on 2009-01-04
Yay! Smart boot manager successfully starts up, but I am having different problems.


First, my hard drive is not listed?? 
When I choose, quit to DOS, I get the GRUB boot menu of my linuxOS. Yay!!
But when I select an option, all I get is: 
> 
Booting 'Arch Linux'
root (hd1,0)
Error 21: Selected disk does not exist
Press any key to continue

When I select the cd-rom drive, all i get is:
Disk error!! 0xAA

I must have disconnected and reconnected drives and floppy stations for hours now, I can hardly take it any longer. 

I saved after having booted the first time, having forgotten to put the disk back in. Does that mean I have to format the disk and do it all over again???

---

### Post by Anaphylaxis on 2009-01-04
Ok, problem solved. The cause of the problem, and all my problems really, was my overlooking the fact that the cd-drives couldn't read any cd-rw's!!!! 

The boot manager booted just fine, but due to the fact that I didn't have any more normal cd's, I tried to install xp on the machine to see if things worked properly. 

After installation was complete, the power supply decided, enough is enough, and committed suicide. 

Oh, the irony. :D

---

