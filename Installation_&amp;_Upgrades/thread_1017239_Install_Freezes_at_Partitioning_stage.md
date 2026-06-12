---
title: "Install Freezes at Partitioning stage"
date: 2008-12-20
forum: Installation &amp; Upgrades
---

### Post by mediumhouse on 2008-12-20
Hi,

I have tried to install Ubuntu 8.04 and Mythbuntu 8.04 from the live CDs and for both of them the install hangs during the part where it is formatting partions [it also says something about getting ext3 file structure or somesuch].  The status bar freezes at 5%.

These live cd's do work in the live environment - I am using the mythbunut one to write this.

I tried installing both using the Alternate CDs [64] and it freezes in the same place but this time at 33%.  I even tried the Ubuntu [32] alternate.

I then tried the Mythbuntu 8.10 live cd to see if a newer version might work but it doesn't even get that far.  It freezes while the white bar is going back and forward across the screen - the live environment fails at a similar place.

This is very frustrating.  I have just built a brand new computer [for a HTPC] and I can't get any of these systems to work.  Can anyone help?

The box has an ASUS p5-em hdmi motherboard, 2gb RAM, 1TB Hard drive, DVICO dual express TV capture card, Samsung DVD drive...

---

### Post by mediumhouse on 2008-12-20
I tried just letting it keep going, after more than half an hour it was still 5%.

The exact place it froze is:

Installing System
Partitions Formatting
5%
Creating ext3 file system for / in partition #1 of SCSI3 (0,0,0)...

---

### Post by tommcd on 2008-12-20
What chipset is on that motherboard? Since it has hdmi, I'm guessing it is a fairly new chipset, so use Ubuntu 8.10, since it has the newest kernel. Use the 32bit alternate CD for the most fail safe install.

Does the computer have Windows on it? If so, then make sure to defragment Windows before partitioning. If you have Vista, use Vista's partitioning tool to make free space to install Ubuntu to.

Make sure you burn the iso at a very slow speed. If you are burning the CD with Windows, use iso recorder or infra recorder, and verify the md5sums after you burn the CD:
[https://help.ubuntu.com/community/BurningIsoHowto/](https://help.ubuntu.com/community/BurningIsoHowto/)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by mediumhouse on 2008-12-20
P5N-EM HDMI with NVIDIA GeForce 7100 / nForce 630i chipset inside supports Intel 45nm

The computer doesn't have windows on it, it is brand new with no operating system of any kind.

Will download the 8.10 32 bit alternate and give that a go.  Might as well, I have downloaded six other variations...

---

### Post by mediumhouse on 2008-12-21
I haven't downloaded the 32 bit 8.10 alternate yet because I am unsure if it will make a difference - though i am trying to source it via other means.  The 64 bit 8.04 live cd works in the live environment, so if it does this, shouldn't it also install?  I am thinking there must be some kind of setting somewhere, perhaps in BIOS, that needs changing but I have no idea really.

---

### Post by mediumhouse on 2008-12-21
Still trying to figure this one out but could this be a problem:

When it freezes, it freezes at this part:

**Creating ext3 file system for / in partition #1 of SCSI3 (0,0,0)...**

I have come across mention that SCSI is a drive type and some systems may see the SATA drive and classify it as a SCSI device.

Could this be the basis of my problem? How do I tell it that it is SATA and not SCSI?

---

### Post by tommcd on 2008-12-22
I still think you should try the Ubuntu 8.10 32 bit alternate install CD for the most fail safe install. The kernel in Ubuntu 8.04 may be having problems with your hard drive controller.

Other than that, perhaps there is a BIOS setting for "legacy IDE mode" or something like that you could use. Check what options you have available in your BIOS.

---

### Post by mediumhouse on 2008-12-25
Being that it was christmas and I had that particular day off work I again had a play with my stubborn HTPC - that's what you do on christmas day, play with toys...

Anyway, I did something I have never done before and instead of using guided partitioning I tried manual [after first finding via a search engine what I should set if I tried manual] and set something like this:

10GB ext3 as /
2GB as Swap
RestGB XFS as /htpc

plus I ticked the box for formatting.

[This was using the Mythbuntu 8.04 64bit live CD]

This actually did the partioning and it started installing. This, as you can imagine, made me happy but that was short lived as it got to 27% and stayed there. I tried the same with the 32 bit Mythbuntu 8.04 Alternate and it froze at 44%.

I didn't try my mythbuntu 8.10 64 bit live cd as I have come to the conclusion that it is flawed and thus will require another download before attempting.

Even though it didn't work, I am slightly more confident that I will eventually get it running. I am still yet to try the Mythbuntu 8.10 32 bit alternate and have a copy of Opensuse 11.1 in the mail] so I still have options.

There is a copy of [the latest?] Mandriva on the cover of a magazine and I tried that too - the live cd part works fine [well it did freeze a couple of times] but it won't install either [I haven't tried the manual partitioning on this one yet].

Before all of this I also downloaded gparted and tried it but I put it in and nothing happens...

Just to clarify a couple of things, this is the hardware I am trying to get working:

Motherboard: Asus P5N-EM-HDMI S775 nF630i FSB1333 DDR2 VGA PCIEx16 HDMI SATA2 [with Gigabyte SPDIF Out add on]
RAM: KINGSTON 2GB KIT 800MHz DDR2 NON ECC 240pin UNBUFFERED DIMM KVR800D2N5K2/ 2G
CPU: Intel BX80571E5200 PENTIUM E5200/ 2.5Ghz/ 2MB CACHE/ 800FSB/ LGA775
DVD: Samsung SH-S223F SATA Black Internal 22x Speed Plus DVD±RW Drive, 12x DVD-RAM
HDD: Samsung 1TB HD103UJ HDD 32MB Cache 1 000GB SATA II 7200rpm, 3.0Gbps 
TV Card: Dvico Fusion Dual Express Hybrid DVI-150
Case: Antec NSK2480B Solution Series MicroATX Desktop Black, EarthWatts 380W PSU

In Bios, the default was for sata to be configured as ide - the other options are raid and ahci - I have tried ahci but not raid.

I haven't done anything with the ide settings, just left them as default - in fact everything is default except the boot sequence as I had to make the cd boot first...

---

### Post by tommcd on 2008-12-26
Some things you can try:
1. Make sure you burn the CDs at a very slow speed; and check the md5sums of the CDs after you burn them.
2. Make sure your RAM is good. Run memtest for a while from one of the Ubuntu live CDs.
3. Can you try a different hard drive? Or perhaps a different sata cable? Run the manufacturer's diagnostic utility on the hard drive to verify that the drive is good. Or test it in a different PC if you can.
4. Remove that TV card and try and install without it. Perhaps it is not supported in linux and is causing problems with the install.

See the reviews on newegg.com for this motherboard titled **Great mythtv board** and **awsome mythtv board**. The first guy says everything works in linux. The second guy says Ubuntu 8.04 works.
[http://www.newegg.com/Product/ProductReview.aspx?Item=13-131-229&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Keywords=(keywords)&Page=1](http://www.newegg.com/Product/ProductReview.aspx?Item=13-131-229&SortField=0&SummaryType=0&Pagesize=10&SelectedRating=-1&PurchaseMark=&VideoOnlyMark=False&VendorMark=&Keywords=(keywords)&Page=1)

---

### Post by mediumhouse on 2008-12-29
Finallly did a memtest and there appeared to be errors on the first of my two RAM sticks so I took it out and replaced it with the one from the second slot.  Re-did the memtest with only the one memory stick in and it passed. I loaded mythbuntu 8.10 32 bit [without concerning myself too much with configuration - I just wanted it to load!] and it went and loaded didn't it? I will have a play with it when I have some more free time but I might need to try one of the other disks I have with one of the other systems because both the live environment and the loaded environment of the 8.10 mythbuntu won't connect to the internet whereas the 64 bit mythbuntu 8.04 live cd would connect to the internet when I used it the other day

---

### Post by ssaammee on 2009-03-07
I have been getting the same error where at 5% during the partition formatting stage of install, my machine would freeze.

I got around this by using the alternate 8.10 image that doesn't have a pretty UI.  It's nice and worked great!

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

### Post by tommcd on 2009-03-08
Glad you got Ubuntu installed! and welcome to the Ubuntu forums!

This is why I suggested (in post #7 of this thread) to use the 8.10 32 bit alternate install CD for the most fail safe install. Glad that helped someone. I hope the OP sees this.

---

