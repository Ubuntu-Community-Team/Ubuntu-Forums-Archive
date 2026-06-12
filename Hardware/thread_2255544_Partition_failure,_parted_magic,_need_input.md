---
title: "Partition failure, parted magic, need input"
date: 2014-12-05
forum: Hardware
---

### Post by Michael_Dullea on 2014-12-05
[COLOR=#444444][FONT=Courier New][I]I rescued a partition to a new drive by image file. With that image on the new drive, it also started with the booting problem. I also noticed the rescue repartitioned the new drive partition. The problem drive has one Parted Magic attribute; “current pending sector count” with a 2 in the raw value. Also another test area said it had an alignment issue.
 
I’ve read that I can clone directly to the new drive without the image method. “Cloning directly to a new disk”   [http://www.technibble.com/guide-using-ddrescue-recover-data/](http://www.technibble.com/guide-using-ddrescue-recover-data/) That would avoid buying a second new drive to get this done. Hopefully this method wouldn’t mess up my partition on the new drive.  
 
My problem is that I get an error message that it can’t find the USB drive, (that is sdc1 labeled OpenELEC). My new drive is sda and the bad one sdb. I’m just going to the main parted magic terminal by not selecting a drive first and then going to that terminal to run the command. I suspect it is looking at one of the two drives and not the USB for adding the logfile. Any ideas? 
 
ddrescue –d –f –r3 /dev/sdb5 /dev/sda6 /media/abcd/openelec/rescue.logfile

Thanks
[/I][/FONT][/COLOR]

---

