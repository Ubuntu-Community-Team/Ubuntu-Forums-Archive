---
title: "Morphing usb stick - any chance of rescue?"
date: 2013-04-04
forum: Hardware
---

### Post by nickdc on 2013-04-04
The story so far, in brief and as far as I remember it:

Brand new Verbatim 4gb NX216 usb stick.
Straight from shop to Humax Foxsat-HDR and used to copy two video recordings.
NX216 travels to different location, is plugged into identical Humax and saved recordings are watched.
Some time later, still in second location, NX216 is again plugged into Humax and one of the video files is copied across to HDD on Humax ... left copying ... and forgotten!
Several hours later, when remembered again, reactivate Humax from screensaver and note no copying still going on, so remove usb stick [possible error no.1: did I exit the file manager first? Pass ...]
Check for copied video on Humax HDD and it's not there. 
Plug usb stick back in and get error message: "Can't read device. Reformat in your pc" 
Plug usb stick into desktop pc running Ubuntu 12.04. It doesn't show up.
Run Gparted and the usb stick shows as sde and 4gb but no partition table.
Run Storage Device Manager which shows the same.
A lot of googling and trying a few things ending up running TestDisk.
TD suggests a damaged partition table ... "Bad Humax". [Checked Verbatim website to confirm NX216 formatted FAT32]
TD creates image.dd successfully (which I still have) but can't retrieve any files.
At this stage, lsusb still lists NX216, but after some further poking around (I confess I've lost track here) it doesn't. When it did list it, it was "Device 013". Now, Device 013 is listed as "GEMBIRD PhotoFrame PF-15-1", which I don't recognise ... could this be the usb stick?
Run Storage Device Manager again, but it doesn't work (sda, b, c & d show in Partition List pane, but the main pane with General Config. and Dynamic Congig. tabs, is greyed out) accompanied by clicking noise from bowels of pc
          [Is this related to the usb problem or an unfortunate co-incidence? Complete removal followed by reinstall of pysdm has made no difference; I'm still without a   functioning Storage Device manager.]
Run Gparted again and now it shows the usb stick as sd**i** and 300**m**b!
Fire up Win XP in Virtual Box and Win XP sees the drive straight away, identifies it as NX216 but says it's not formatted. Also says it's 300mb [I think].
More googling brings this heplful post: [http://askubuntu.com/questions/177519/usb-flash-drive-mount-issue](http://askubuntu.com/questions/177519/usb-flash-drive-mount-issue)
So I run    <tail -f /var/log/syslog>  plug in the usb stick and this is the output:

```
nick@nick-build-1:~$ tail -f /var/log/syslog
Apr  4 19:13:29 nick-build-1 kernel: [ 3767.582407] sd 8:0:0:0: [sdi] No Caching mode page present
Apr  4 19:13:29 nick-build-1 kernel: [ 3767.582416] sd 8:0:0:0: [sdi] Assuming drive cache: write through
Apr  4 19:13:29 nick-build-1 kernel: [ 3767.587436] sd 8:0:0:0: [sdi] No Caching mode page present
Apr  4 19:13:29 nick-build-1 kernel: [ 3767.587445] sd 8:0:0:0: [sdi] Assuming drive cache: write through
Apr  4 19:13:29 nick-build-1 kernel: [ 3767.592459]  sdi: unknown partition table
Apr  4 19:13:29 nick-build-1 kernel: [ 3767.595164] sd 8:0:0:0: [sdi] No Caching mode page present
Apr  4 19:13:29 nick-build-1 kernel: [ 3767.595171] sd 8:0:0:0: [sdi] Assuming drive cache: write through
Apr  4 19:13:29 nick-build-1 kernel: [ 3767.595175] sd 8:0:0:0: [sdi] Attached SCSI removable disk
Apr  4 19:17:01 nick-build-1 CRON[18922]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr  4 19:19:24 nick-build-1 kernel: [ 4122.916217] usb 1-5.4.4: USB disconnect, device number 13
Apr  4 19:36:15 nick-build-1 kernel: [ 5133.791164] usb 1-5.4.4: new high-speed USB device number 14 using ehci_hcd
Apr  4 19:36:15 nick-build-1 kernel: [ 5133.878151] scsi9 : usb-storage 1-5.4.4:1.0
Apr  4 19:36:15 nick-build-1 mtp-probe: checking bus 1, device 14: "/sys/devices/pci0000:00/0000:00:1d.7/usb1/1-5/1-5.4/1-5.4.4"
Apr  4 19:36:15 nick-build-1 mtp-probe: bus: 1, device: 14 was not an MTP device
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.880741] scsi 9:0:0:0: Direct-Access     NX216    FLASH READER     1.0E PQ: 0 ANSI: 2
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.882239] sd 9:0:0:0: Attached scsi generic sg10 type 0
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.884363] sd 9:0:0:0: [sdi] 614401 512-byte logical blocks: (314 MB/300 MiB)
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.885230] sd 9:0:0:0: [sdi] Write Protect is off
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.885239] sd 9:0:0:0: [sdi] Mode Sense: 03 00 00 00
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.885975] sd 9:0:0:0: [sdi] No Caching mode page present
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.885984] sd 9:0:0:0: [sdi] Assuming drive cache: write through
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.891343] sd 9:0:0:0: [sdi] No Caching mode page present
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.891354] sd 9:0:0:0: [sdi] Assuming drive cache: write through
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.896043]  sdi: unknown partition table
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.898936] sd 9:0:0:0: [sdi] No Caching mode page present
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.898944] sd 9:0:0:0: [sdi] Assuming drive cache: write through
Apr  4 19:36:16 nick-build-1 kernel: [ 5134.898950] sd 9:0:0:0: [sdi] Attached SCSI removable disk
Apr  4 19:39:01 nick-build-1 CRON[25534]: (root) CMD (  [ -x /usr/lib/php5/maxlifetime ] && [ -d /var/lib/php5 ] && find /var/lib/php5/ -depth -mindepth 1 -maxdepth 1 -type f -cmin +$(/usr/lib/php5/maxlifetime) ! -execdir fuser -s {} 2>/dev/null \; -delete)
```

That's where I am now. I don't want to format a 4gb drive to 300mb, or risk any further damage/corruption till I have a better idea of what may have happened and what my recovery options are. Ideally, I want to save those two video files if I possibly can. But the bottom line is at least to regain the full 4gb pendrive. (For the hell of it - I know it would hardly break the bank to replace it!)

Could someone kindly suggest a way forward?

And ideas about my non-functioning Storage Device Manager would be welcome too.   
:confused:

---

### Post by dabl on 2013-04-04
> **nickdc said:**
> The story so far, in brief and as far as I remember it:
.
.
.
Some time later, still in second location, NX216 is again plugged into Humax and one of the video files is copied across to HDD on Humax ... left copying ... and forgotten!


Obviously, the stick was removed before this happened -- I wonder whether "safely remove" or "eject" was used?  Probably not.  :(

> 
.
.
.
Plug usb stick back in and get error message: "Can't read device. Reformat in your pc" 
Plug usb stick into desktop pc running Ubuntu 12.04. It doesn't show up.
Run Gparted and the usb stick shows as sde and 4gb but no partition table.
Run Storage Device Manager which shows the same.

Doesn't matter about all the rest of the story -- the damage was already done.

> 
Could someone kindly suggest a way forward?



Depending on the condition of the USB stick, unless you want to pay big $$ for a professional forensic recovery project, I would say cut your losses, and

```
dd if=/dev/null of=/dev/sdX bs=512 count=1
```

where "X" is your device number when it is plugged in your computer, as shown by "fdisk -lu".

This will provide you a new, blank device, upon which you can set a partition table, make a partition, format it FAT32, and try again, this time remembering to "safely remove" before the stick gets yanked out of the computer.

---

### Post by nickdc on 2013-04-05
> ```
 	 	
dd if=/dev/null of=/dev/sdX bs=512 count=1 

```where "X" is your device number when it is plugged in your computer, as shown by "fdisk -lu".

This will provide you a new, blank device, upon which you can set a  partition table, make a partition, format it FAT32, and try again, this  time remembering to "safely remove" before the stick gets yanked out of  the computer.

Thanks for the suggestion but running that code hasn't changed anything: Gparted shows exactly the same as before - a drive "sdi" with 300Mb unallocated space. I'm worried that if I format it now it could make the loss of the 3+ Gb even more permanent. I'm wondering if the fact of the change from sde to sdi is significant: I have four hard drives in the pc - sda, sdb sdc & sdd. When I first plugged in the usb stick it showed as sde; now it shows as sdi. Is there some way in which the jump from "e" to "i" corresponds to the "missing" capacity of the drive?

> Obviously, the stick was removed before this happened -- I wonder whether "safely remove" or "eject" was used?  Probably not.

For the record, with the Humax box there is no "safely remove". When files have finished copying the indicator goes from the screen and it is then safe to remove the drive. The Humax recognises this with an acknowledgement on screen: "USB drive has been disconnected". That's exactly what happened in this case. The only difference from previous occasions (with other usb drives - this one had not been used before) was the length of time I left it connected, after it had finished copying ... if it did ever finish copying. But the screen indicator had cleared there was nothing to indicate anything amiss ... until I plugged the drive back in. On a pc I'm always very careful about properly removing usb devices. I've learned the hard way!

---

### Post by dabl on 2013-04-05
> **nickdc said:**
> Thanks for the suggestion but running that code hasn't changed anything: Gparted shows exactly the same as before - a drive "sdi" with 300Mb unallocated space.

My bad -- I should have said "prefix this command with 'sudo' and make double-certain you have the USB stick ID correct".  That dd command will zeroize the master boot record and partition table -- Gparted will see it as an empty, unformatted device (unless there has been damage to the flash media itself).

---

### Post by nickdc on 2013-04-06
Thanks. Yes, I'd figured it should run with sudo, but still no joy. I have made some further progress though, following suggestions on other threads, and at least the drive is still being seen by Ubuntu and now it's back to its full 4gb, showing in Gparted as unallocated space. But nothing happens when I try to write a partition table - there's a pause, it seems to be working, no error message, but then when gparted has finished its renewed scan of the drives, it shows it in exactly the same state as before. Late yesterday I thought I'd had success using cfdisk, which reported that a new partition table was definitely written to the drive. But actually no evidence of that - still no access, still gparted showing no partition table ... Maybe as you suggest, dbl, there's actual hardware damage. On the software side there doesn't seem much left to try.

---

### Post by dabl on 2013-04-06
> **nickdc said:**
> But nothing happens when I try to write a partition table - there's a pause, it seems to be working, no error message, but then when gparted has finished its renewed scan of the drives, it shows it in exactly the same state as before.

I have never seen that, in several dozen USB stick projects -- I fear you've got a piece of dumpster food on your hands.  :(

As a last resort, and if you have time on your hands, there's a free Windows [**[color=green]utility from HP[/color]**](http://files.extremeoverclocking.com/file.php?f=197) that I have used on a stubborn stick to get rid of the "U3" faux CD ROM thing.

---

### Post by nickdc on 2013-04-07
Yep, I've even tried the HP formatter, with no success. It just produces an error message: "unable to format drive" or something similar.

> I fear you've got a piece of dumpster food on your hands.  :sad:

I've come to the same conclusion. When I'm next in the area I shall return it to the retailer from whom it was purchased. They're pretty good, and I expect I'll get a replacement, which I shall keep well away from my Humax box! Thanks again for your help in trying to rescue this one.

---

