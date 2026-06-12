---
title: "Can external hard disk be used to run the OS"
date: 2015-11-25
forum: Hardware
---

### Post by mastablasta on 2015-11-25
Can one of the small external drives actually be used to successfully run Linux. Something like the small WD Essentials?

I know that the WD green drives really can't be used as they power down (spin down) a lot. they are OK for data , but running the OS from them can be problematic. so, could this kind of external drive be used to boot from and then run the OS? or would they too keep power down making it impossible to run the OS well?

---

### Post by v3.xx on 2015-11-25
I use to run multiple HDDs by installing grub on each HDD and using bios to select which disk to boot.  This way any hdd can be pulled without lost of boot capabilities.

---

### Post by sudodus on 2015-11-25
I use external HDDs a lot for booting and testing linux operating systems, both 'persistent live' and 'installed' :-)

In order to get good read/write speed I prefer eSATA and USB 3, but USB 2 is also good. Usually USB pendrives have slow flash hardware, which is limiting the speed more than the USB 2 communication. So a hard disk drive or SSD in an external box via USB 2 is faster than most pendrives, even many USB 3 pendrives (particularly when writing many small files).

I don't know the problems with WD green drives, but I have used many different HDDs and SSDs externally via a ***separate eSATA and USB 3 box***. I have such a box for 2.5" drives and another one for 3.5" drives, and they have no problem with booting. If you want to, I can tell you the brand name and models.

-o-

I have had problems with a Toshiba HDD in a closed external box. I think there is some special software, maybe similar to what you describe for the WD green drives. Sometimes the system get corrupted at shutdown, so it does not want to boot (but it works well as a storage disk).

---

### Post by mastablasta on 2015-11-26
wd green drives sometimes won't spin back up or would spin down when they should actually be working. I am not sure if this was solved in any way.
not so long ago we wanted to replace the old 10 GB OS drive that seemed to be failing with a WD green. OS would sometimes boot sometimes it got stuck, various errors and all. though about returning the disk but before we did we decided to stick it in another PC as data drive. works perfect to this day. I read similar stories so I was wondering if these UBS powered drive also did the same. 

the server is acting strange so I think I will try with a USB stick from another company first. as soon as stuck 2 USB devices it wouldn't boot, no matter what I told him and which device I said to boot from use. though it did boot when I added old Toshiba. so I think I will try another USB key first. I wanted to add a hard disk or possibly use an external disk for OS. either way I need to figure out how to backup the whole OS flash drive during weekend automatically. and before this one get's corrupted as well.

---

### Post by Skaperen on 2015-11-26
> **mastablasta said:**
> as soon as stuck 2 USB devices it wouldn't boot, no matter what I told him and which device I said to boot from use. though it did boot when I added old Toshiba. so I think I will try another USB key first. I wanted to add a hard disk or possibly use an external disk for OS. either way I need to figure out how to backup the whole OS flash drive during weekend automatically. and before this one get's corrupted as well.
what about not plugging in the data drive until after the OS is up and running from the memory stick?

---

### Post by sudodus on 2015-11-26
> **Skaperen said:**
> what about not plugging in the data drive until after the OS is up and running from the memory stick?

+1

This is probably possible.

Another alternative is to connect the the OS via eSATA. At least in desktop computers with SATA ports it is easy with a cheap 'plate', for example [2 Port SATA to eSATA Slot Plate Bracket](http://www.startech.com/Cables/Drive/eSATA/2-port-SATA-to-ESATA-Slot-Plate-MF~ESATAPLATE2)

---

### Post by mastablasta on 2015-11-27
if I plug it after it boot it all works as it should. but then it means someone has to be at home to remove the drive when the server is rebooted so that it would actually boot.

actually I have e-sata exit on the back.

then I would need some external enclosure with e-sata exit. or do they have SATA to e-sata adapters? and would it work good?

---

### Post by Skaperen on 2015-11-27
what kind of boot failure is happening?  a BIOS failure?  does the boot loader come up?  does the kernel get loaded and started?  any error messages?  init failure?

---

### Post by mastablasta on 2015-11-28
it doesn't get to GRUB. looks like BIOS stops it or rather BIOS tries to boot from the disk but finds no OS present and stops (i forgot at the moment, since i haven't tried it for a couple of months). in any case it doens't get to GRUB. hmm maybe i could stick another grub to the other disk. but as i remember when we tried to boot into live session from another USB port it just said there was no OS disk. the internal USB is ment for tape but it can also boto frm it. there are 6 ports outside so it owudl be a shame not to use them. at least for some secondary disk/backup. but as i remember the issue was with Flash drives only.

---

### Post by Skaperen on 2015-11-28
sounds like BIOS is probing the drives and getting the big data drive as the first one and trying to boot that one.  try to redo the BIOS setup to select the drive with *both* devices plugged in and see if it gives a choice, if not, do the BIOS drive select steps with *only* the memory stick plugged in and see if this selects the memory stick for booting with both plugged in.  one of my computers i tried this with would *not* do it ... it would not recognize or remember specific drives ... so i know that a BIOS issue is a distinct possibility.  try reversing how the devices are plugged in.  there are a *lot* of USB to (e)SATA converters on the market, if you are willing to try that.  if you do, be sure it is USB 3.0 and provides power (some don't). maybe your BIOS will select (e)SATA first for booting or let you choose it.  else try to install the OS on the big drive. my external WD drives do spin down but will spin back up with the next command to it (delays that operation by about 3 seconds).  i have Slackware on one and it works OK.

---

