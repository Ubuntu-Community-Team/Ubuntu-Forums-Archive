---
title: "Remove the Language selection at boot up (USB using LiveCD)"
date: 2009-05-15
forum: Installation &amp; Upgrades
---

### Post by kerplatz on 2009-05-15
Hi,

Here is the problem. I cannot figure out how to get the language selection to go away (it is annoying) every time Ubuntu boots up. There is more to the story so read on.

I bought a 16Gig USB flash drive so I could do 2 things. One, have an OS that I could take with me to school when I did not want to lug around my laptop. Two, have about 10Gig of file storage for whenever I needed it.

I Installed Ubuntu from Vista onto the USB drive (there was a website that gave me the directions). This worked great except for one thing, I could not access the files I put on the drive in folders outside of Ubuntu. This was not the desired behavior. The install was persistent and I did not have to answer which language I wanted to use every time it booted. So I went looking for another way to do this.

Here is what I was able to accomplish. I made in Ubuntu on another computer 2 partitions on the USB drive. Both are FAT32. Since Windows can only see the first partition, I put my file storage there (I don't care to access the linux files in Windows) and Ubuntu on the second partition and made that one bootable. I then put Ubuntu using the LiveCD onto the second partition. But, to my horror it was not persistent, however I knew that it could be done.

So, I installed the original Ubuntu files back to the first partition and booted into Ubuntu from another computer so I could look at files. I then copied all the files that were different including the casper-rw file to the second partition.

I now have Ubuntu booting and persistent from the second partition on the USB drive. My only problem which is more of an annoyance is that it keeps asking for my language every time it boots. I know that it must be in some config file or other file because the first install to the USB drive installing from Vista did not have that language selection at boot up.

I am very happy with the way Ubuntu is working except for that annoyance. Can anyone tell me how to turn it off? Thank you.

PS - I have researched this whole process of putting Ubuntu on a USB drive that has more then one partition for about a week and as far as I can tell, I may be the only person to have accomplished this!!! I will be happy to give anyone the full details if they want them, but I suspect that I have given enough info for most of you to get it without any more help.

---

### Post by Mighty_Joe on 2009-05-15
The only way I could figure out how to get rid of that menu was to do a full Ubuntu install to the USB drive. I ran into a few problems with the Live CD tool which drove me to a full install as well.
I was *planning *on doing two partitions on my drive, but I wanted the windows-accessible partition to mount as /home, and the partition tool wouldn't let me.

---

### Post by kerplatz on 2009-05-15
This might help solve my problem, but I am not going to reinstall it again. I will just live with this until I find out how to get rid of the language menu. I am positive it is just a line in some config file in the boot files. Thanks for your help.

---

### Post by sailthesea on 2009-05-15
Thats a tidy job! 
 I'd live with the language issue because you can't really alter the image of a LiveCD 
 It seems to be doing everything else you want

---

### Post by squirrelpimp on 2009-06-20
Hi,

try placing a file called "lang" inside the syslinux folder on your usbkey. The file must only contain one line specifying the selection to be made on the language-dialog, e.g. "de".

regards, lars

---

