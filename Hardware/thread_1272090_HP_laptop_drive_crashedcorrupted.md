---
title: "HP laptop drive crashed/corrupted"
date: 2009-09-21
forum: Hardware
---

### Post by Silvernail on 2009-09-21
I need some help. One of the girls down at the diner where I eat has several kids who do not worry when the WOT warning pops up. So now her computer as a fist full of viruse. She and someone took the hard drive out of he HP Pravillion laptop and sent it to Tracies brother to fix. He is suppose to have done so but it would not boot when it was reinstalled in the laptop.

I offered to try and resurect it from the dead by installing a linux system on it.

The live CD works great.
When I go to install I get to the partition part and it shows blank. This is on 7.04, 8.04, and 9.04.

When it is trying to boot with no Ubuntu CD in the drive, this error message is produced.
PXE-E6 memory test failure, Check cable.
PXE-MOF exiting ????-ROM

When the CD is booting, this error message appears early in  the process.
Booting From Local Disk
isolinux: Disk error 81, AK=8281

Trying:
```
gparted /dev/sda
```
returns a device is locked.

Using:
```
lspci -v
``` shows that the IDE statis as 'access denide'

I'm trying to get 'dmesg' here but recognizing a flash drive on that computer is problematical, sometimes and sometimes not.

I'm not sure where to go from here and would appredite some suggestions.

Thanks.
Dave

---

