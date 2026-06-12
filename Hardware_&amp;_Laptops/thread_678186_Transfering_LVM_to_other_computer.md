---
title: "Transfering LVM to other computer"
date: 2008-01-25
forum: Hardware &amp; Laptops
---

### Post by JohnDear on 2008-01-25
Hello all,

I am not much of a Linux expert, but I have managed to run Linux in a "quasi server" environment. Now, I have decided to get a better motherboard and a faster processor (Celeron to C2D so major chipset change). I don't have a problem reinstalling Linux, all it basically does is sit and serve media to the network, so there are not files that need saving from the main drive.

Now, my LVM is a totally different situation. I have close to 3 TB of data in an LVM with 4 drives, and those I really can't lose. Can I just disconnect that and plug it into a new computer? Do I have to back something up first? I think there is a file with LVM data somewhere, but I am not sure if I have to do something about that.

Any help is greatly appreciated
John

PS: This is the right forum for this, right?

---

### Post by jeffus_il on 2008-01-26
The Linux kernel can boot after changing hardware, take the livecd as an example. I would try it, You could make sure that you have support for the new hardware before you shut down the old machine, that is if the necessary kernel modules are installed. If you are comfortable working at the text console, you should be able to do it.

---

### Post by JohnDear on 2008-01-26
Hi Jeffus,

thanks for the reply. So the OS may work, but what if it doesn't? 

If I have to reinstall, what am I doing with my LVM? Any precautions I need to take?

John

---

### Post by jeffus_il on 2008-01-26
I guess I would make sure that the LVM software to be installed is backward compatible with  your current version.
Do you have a backup of the LVM?
I found this on moving a volume group to another system, Which would be relevant if you installed a new system:
[http://tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html](http://tldp.org/HOWTO/LVM-HOWTO/recipemovevgtonewsys.html)

---

### Post by JohnDear on 2008-01-26
Well, I did not export my volume group. According to the page you linked it is not necessary. Now, if I do "pvscan", I get:
  Couldn't find device with uuid 'uwcDst-NCXr-vEqC-2DFD-0Me4-iZdn-meeSWS'.
  Couldn't find device with uuid 'IhIVJ9-L5Bj-1Jut-V5fL-w426-2TWq-0HwMaJ'.
  Couldn't find device with uuid 'uwcDst-NCXr-vEqC-2DFD-0Me4-iZdn-meeSWS'.
  Couldn't find device with uuid 'IhIVJ9-L5Bj-1Jut-V5fL-w426-2TWq-0HwMaJ'.
  Couldn't find device with uuid 'uwcDst-NCXr-vEqC-2DFD-0Me4-iZdn-meeSWS'.
  Couldn't find device with uuid 'IhIVJ9-L5Bj-1Jut-V5fL-w426-2TWq-0HwMaJ'.
  Couldn't find device with uuid 'uwcDst-NCXr-vEqC-2DFD-0Me4-iZdn-meeSWS'.
  Couldn't find device with uuid 'IhIVJ9-L5Bj-1Jut-V5fL-w426-2TWq-0HwMaJ'.
  Couldn't find device with uuid 'uwcDst-NCXr-vEqC-2DFD-0Me4-iZdn-meeSWS'.
  Couldn't find device with uuid 'IhIVJ9-L5Bj-1Jut-V5fL-w426-2TWq-0HwMaJ'.
  Couldn't find device with uuid 'uwcDst-NCXr-vEqC-2DFD-0Me4-iZdn-meeSWS'.
  Couldn't find device with uuid 'IhIVJ9-L5Bj-1Jut-V5fL-w426-2TWq-0HwMaJ'.
  PV /dev/sdb1        VG server   lvm2 [465.76 GB / 0    free]
  PV /dev/sda1        VG server   lvm2 [465.76 GB / 0    free]
  PV /dev/sdd1        VG server   lvm2 [698.63 GB / 0    free]
  PV unknown device   VG server   lvm2 [167.68 GB / 8.00 MB free]
  PV unknown device   VG server   lvm2 [232.88 GB / 0    free]
  Total: 5 [1.98 TB] / in use: 5 [1.98 TB] / in no VG: 0 [0   ]

I think my mistake is, that I have a weird setup, probably due to my inexperience. I have one big volume group, which includes 5 drives. 3 of those drives are in one volume group and the other 2 a another volume group.
Unfortunately, right now I can only use the set of 3, because I am an idiot and didn't realize that new motherboards only have 1 PATA connector and I have the system disk and the set of 2 as PATA.

That seems to make the restore pretty inconvenient, and I am not sure what to do now :-(

Any ideas?

---

### Post by jeffus_il on 2008-01-27
Would you want to purchase a PCI IDE card? They are very reasonable.
Another option is to put them into an external USB-2 enclosure.

---

### Post by JohnDear on 2008-01-28
Yeah, I considered that. I spend a whole night ruminating about this, and I came to the conclusion that I need to get rid of the 2 old PATA drives. But in order to do that I have to get the volume group up and running again. So I did what I had to do, I removed the new hardware and put the old crap back in, reconnected all the drives. I freed up a 250 GB drive in one other computer and made some more room on other drives, and I spend all of yesterday and half of today to move 430 GB through my network. 
I am about done now and will then remove the logical volume with the two PATA drives from the volume group. Then I can take the old hardware out, put the new stuff back in and hope I can get it back up and running.

I already had to manually reconfigure the xserver because I am switching between ATI and NVidia....

I can do it, I can do it :-)

Thanks for your help

---

