---
title: "Toshiba Tecra S1"
date: 2005-03-10
forum: Hardware &amp; Laptops
---

### Post by Cturtle on 2005-03-10
Hello,

I consider buying a Tecra S1. In the shop I tried the Warty Live CD on this machine and got a Grub error. Does anyone know if Warty will run on the Tecra S1?

Regards,

Jan

---

### Post by bourlas on 2005-03-16
yes it does !!! but there is a problem with the livecd, the error you said
I 've managed to install hoary array5 and everything seems fine

as for the grub error there is a solution that you must boot with the iso
of sbm (smart boot manager a sourceforge project) and choose cd boot
and then change your cd to the live ubuntu cd and everything works
fine

I had the same problem with the live cd of mepis.org
because mepis site is down these days search their forums 
for cd boot problems and you will find the link to the bootable
iso of sbm

---

### Post by TmP on 2005-09-15
HI!
I also own a Tecra S1.
After trying the Hoary LiveCd, I've decided to install it.
My first idea was to change the partition size. I happened to have a mandriva install, which was supposed to allow partition resizing. It got frosen in the middle of it, leaving me biting my nails in fornt of a please wait screen for a couple of hours [-o< ( and the HDD was warking hard all this time). I found the courage to reboot it and it did not delete anything on my disk.

Than I decided to do it the hard way. Tecra's have an preinstalled 2 or 3 20GB partitions, and both of them in fat32 (although there is a program supplied that allows you to change it to NTFS)
.
And so I got to recording cd's.. 18GB of them.
After a boring weekend, I had an empty partition.
I've burned the Hoary install on a cd and got to work at it.

In the boot: prompt I had to give the linux vga=771 parameter, or the screen would blink.
From the installer, Iv'e deleted the second, non win install 20GB partition,
created a 256mb swap partition, a 6GB root and 4GB of Home. The remaining 10 GB, I've left in fat32.

The installation went smoove, 

Graphics and sound are 100% ok.
Suspend isn't working, neither is hibernation ( not in the windows way ).
Touchpad doesnt come with the cool functions like scrolling on the edges ( or not out of the box - Im still figuring this one out)
Speed step works, but you dont have any influence over the usage or the processor. Sometimes it freezes in the lowest power  setiing - the computer runs slow because it's using 600Mhz out of 1600 available.

Ive tried Breezy liveCD.
It works and is better.
But id wait for the official release if i ware you.

Last notice.
Dont buy Tecra if you want a stress free life. Its VERY faulty
I've had it serviced 3 times - each time a TOTAL replacement of the motherboard.
And a week after I've installed Ubuntu, the HDD got screwd. I've bought a new one and its operation temperature is somewhat disturbing.

On the other hand it's got everything you need. Great processor, great graphics card with separate 32mb of ram, and you can get it at a good proce nowadays.
 
That is all.

---

