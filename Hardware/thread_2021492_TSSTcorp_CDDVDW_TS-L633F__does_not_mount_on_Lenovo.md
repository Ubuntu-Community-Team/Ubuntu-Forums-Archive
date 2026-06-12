---
title: "TSSTcorp CDDVDW TS-L633F  does not mount on Lenovo V570"
date: 2012-07-09
forum: Hardware
---

### Post by fenris666 on 2012-07-09
Last January I installed UBUNTU 11.10 on a new V570 Lenovo. I installed using a usb stick and removed the pre-installed Windows from the machine.

I did not at the time use the CD drive  (a TSSTcorp CDDVDW TS-L633F) but eventually
noticed that it did not seem to be working properly. I never spent time on this, since I did not need to use the drive until recently when I tried to read a Linux Format DVD. - Then I realized the drive does not mount, even when I have a legit DVD in it. 

Disk Utility finds it, and if I examine the syslog after starting up, the drive seems 
to be found and attahced normally:

>Jul  9 04:10:55  kernel: [    2.268315] ata5.00: ATAPI: TSSTcorp CDDVDW TS-L633F, LE02, max UDMA/33
>Jul  9 04:10:55  kernel: [    2.275504] ata5.00: configured for UDMA/33
>Jul  9 04:10:55  kernel: [    2.283805] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW TS-L633F  LE02 PQ: 0 ANSI: 5
>Jul  9 04:10:55  kernel: [    2.293165] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
>Jul  9 04:10:55  kernel: [    2.293176] cdrom: Uniform CD-ROM driver Revision: 3.20
>Jul  9 04:10:55  kernel: [    2.293360] sr 4:0:0:0: Attached scsi CD-ROM sr0

But it does not automount and when I try to manually mount it I get an error message:

   $ sudo mkdir /media/dvd
   $ sudo mount /dev/cdrom /media/dvd
   mount: no medium found on /dev/sr0


The medium is fine, I have also tried similar with music CD's that I know to work, so it is 
something to do with the drive. I even tried booting from a live DVD, but the bootloader did not go for the DVD drive, even though it was first in the boot order.

I have seen one similar message regarding this drive 
([http://ubuntuforums.org/archive/index.php/t-1846298.html](http://ubuntuforums.org/archive/index.php/t-1846298.html))
but in that case, any  DVD content is shown as a blank disk, in my case the DVD/CDs are simply ignored.

Does anyone have an idea how I can get the drive working, or check what is the problem if it truly is problematic...

Sincerely

---

