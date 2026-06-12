---
title: "Installing 8.04 on Macbook, no bootable disk"
date: 2008-05-16
forum: Hardware
---

### Post by pmatos on 2008-05-16
Hello all,

I have removed all partitions from my macbook, created a new 30gb partition for leopard and the rest for ubuntu. I installed refit and then went for ubuntu installation with the 64bit cd i just received in my mailbox. The installation went fine but then it says that there is no bootable linux disk. I thought it was because there's a swap partition and refit gets confused so I installed ubuntu without swap but same thing happens.

Any suggestions?

Cheers,

Paulo Matos

---

### Post by Apple Ink on 2008-05-17
If you can reformat your drive, then it is suggested you use BootCamp to partition your drive! 

Once you have partitioned using bootcamp, select install later and close BootCamp. Launch Activity Monitor and terminate any BootCamp processes running (there shouldn't be any though!). 

Insert Ubuntu disk and restart. Just after the screen turns white, press c and install normally!

DO NOT MAKE ANY SWAP PARTITION!!!

Restart and press alt/option after the white screen! Choose Windows from the boot options. And ta-da!

You dont need rEFIt at all!

Ive just done the same n my MacBook 3 days ago.
Any problems, message me. If you want t create a swap file in your root folder itself, message me and ill post a new reply!

---

### Post by Apple Ink on 2008-05-17
If you can reformat your drive, then it is suggested you use BootCamp to partition your drive! 

Once you have partitioned using bootcamp, select install later and close BootCamp. Launch Activity Monitor and terminate any BootCamp processes running (there shouldn't be any though!). 

Insert Ubuntu disk and restart. Just after the screen turns white, press c and install normally!

DO NOT MAKE ANY SWAP PARTITION!!!

Restart and press alt/option after the white screen! Choose Windows from the boot options. And ta-da!

You dont need rEFIt at all!

Ive just done the same in my MacBook 3 days ago.
Any problems, message me. If you want t create a swap file in your root folder itself, message me and ill post a new reply!

---

### Post by cyberdork33 on 2008-05-17
> **pmatos said:**
> Hello all,

I have removed all partitions from my macbook, created a new 30gb partition for leopard and the rest for ubuntu. I installed refit and then went for ubuntu installation with the 64bit cd i just received in my mailbox. The installation went fine but then it says that there is no bootable linux disk. I thought it was because there's a swap partition and refit gets confused so I installed ubuntu without swap but same thing happens.
There is a bug in the Hardy installer. just sync the partitions in rEFIt after installing:
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

Please visit the Apple Users forum in the future!

---

