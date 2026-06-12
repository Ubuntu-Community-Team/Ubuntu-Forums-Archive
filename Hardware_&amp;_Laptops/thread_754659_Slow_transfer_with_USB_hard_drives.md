---
title: "Slow transfer with USB hard drives"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by kahlil88 on 2008-04-14
Transferring files to USB devices is suddenly really slow (like 1.5 MB/s, maybe less). How can I fix this?

---

### Post by mlapaglia on 2008-04-14
are you using usb 1 or 2.0? if usb 2.0 does the computer know you are using 2.0?

---

### Post by kahlil88 on 2008-04-14
It's a USB 2.0 port, and the drive properties window says **USB 2.0 at 12 Mbps**. It wasn't always so slow, this started happening pretty recently. One day, I couldn't get my drives to mount at all, and then I tried using ** modprobe -r ehci_hcd** or **rmmod ehci_hcd** and it finds drives, but at this painfully low speed!

---

### Post by MiCovran on 2008-04-14
12 Mbps actually IS 1.5 MBps. Bit is 8 times smaller than byte.

So your problem is probably got something to do with ubuntu recognizing your drive or USB port speed. Not that I know how to help you, though. :(

Maybe someone else does.

---

### Post by kahlil88 on 2008-04-15
So how can I fix this? I've found several threads about slow USB, but so far none of them have helped me solve my problem. I tried **cat /proc/bus/usb/devices** but I just get a "no such file or directory" error. I hate using it at USB 1.0 speed, and I don't understand why it would suddenly do this.

---

### Post by kahlil88 on 2008-04-25
I'm still having this problem with a CLEAN install of Hardy Heron. Any ideas?

---

### Post by buggs187 on 2008-04-25
I have the same problem. All USB connections seem to be running at a snails pace. I have tried 2 different USB Hard Drives and 3 Different Pen Drives and they are all slow (500kb/s - 934kb/s). Using 8.04 Final. All Devices are USB 2.0 and work fine under Windows "As much as I hate to admit it". This problem occurred in the last release as well.
I seen a post about synchronous settings but have been unable to fine a option to change in Hardy "Missing Package/Need to install a Package?".

Any Help PLEASE?

Dmesg
```
[36805.086359] USB Mass Storage support registered.
[36805.087792] usb-storage: device found at 3
[36805.087795] usb-storage: waiting for device to settle before scanning
[36810.092642] usb-storage: device scan complete
[36810.100029] scsi 4:0:0:0: Direct-Access     WDC WD50 00AAKB-00UKA0    0000 PQ: 0 ANSI: 0
[36810.124199] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[36810.137237] sd 4:0:0:0: [sdb] Write Protect is off
[36810.137258] sd 4:0:0:0: [sdb] Mode Sense: 27 00 00 00
[36810.137263] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[36810.148193] sd 4:0:0:0: [sdb] 976773168 512-byte hardware sectors (500108 MB)
[36810.161180] sd 4:0:0:0: [sdb] Write Protect is off
[36810.161191] sd 4:0:0:0: [sdb] Mode Sense: 27 00 00 00
[36810.161194] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[36810.161202]  sdb: sdb1
[36810.179299] sd 4:0:0:0: [sdb] Attached SCSI disk
[36810.179353] sd 4:0:0:0: Attached scsi generic sg2 type 0

```

lsusb
```
Bus 002 Device 003: ID 04b4:6830 Cypress Semiconductor Corp. USB-2.0 IDE Adapter
Bus 002 Device 002: ID 108b:0005 Grand-tek Technology Co., Ltd 
Bus 002 Device 001: ID 0000:0000  

```

---

### Post by buggs187 on 2008-04-25
I also want to add that every time that I plug a USB storage device in I have to issue the command ```
rmmod ehci_hcd
``` Other wise They do not mount when they are inserted.

---

### Post by elperepat on 2008-04-26
> **kahlil88 said:**
> Transferring files to USB devices is suddenly really slow (like 1.5 MB/s, maybe less)...

Same thing here. When transfering large files, I get a decent speed at the beginning of the transfer, but after a few seconds, it drops back to 0.9-1.2M/s. I tried different flash drives and the reaction is the identical. Same file transfer in Windows averages at 10M/s for the whole transfer.

Hardy, fresh install. USB2.0 for sure. Speed was fine on Gutsy.

---

### Post by kahlil88 on 2008-04-27
Turns out my issue is hardware related...it was time to upgrade anyway.

---

### Post by buggs187 on 2008-04-28
I wish it was as simple as replaceing a piece of hardware. I am using a HP DV6110us Notebook. So that's not going to help me :( 

I will try Kubuntu and see of i have the same problem and some other distro as well. I really want to get this fixed.

---

### Post by buggs187 on 2008-05-01
Ok I have tried formating one usb drive from fat32 to NTFS and had the same slow results. After 100-200mb it reduces the speed to 800-900kb/s.. So it's not the format that counts.

---

### Post by buggs187 on 2008-05-08
Still can't figure it out. I have tried different drives and formats but always end up with slow transfers. Anyone have a clue please ???? :(

---

### Post by Whiffle on 2008-05-08
What usb modules are loaded?  It seems to me like theres something wrong with your kernel/drivers.

I just copied a 700 MB file from my external USB 2.0 hard drive on arch to my computer and it ran about 22 MB/s without  any problems.

---

### Post by elperepat on 2008-05-09
> **buggs187 said:**
> Still can't figure it out. I have tried different drives and formats but always end up with slow transfers. Anyone have a clue please ???? :(

Just to let you know you're not alone. I still have the same issue: Fast for the first 100meg or so, then slow.

> What usb modules are loaded? It seems to me like theres something wrong with your kernel/drivers.

How do I do that? is "lsmod | grep usb" OK?

```
usb_storage            82496  1 
libusual               23520  1 usb_storage
usbhid                 35168  1 
hid                    44992  1 usbhid
scsi_mod              178488  6 usb_storage,sg,sr_mod,sd_mod,sbp2,libata
usbcore               169904  7 usb_storage,libusual,usbhid,ohci_hcd,ehci_hcd

```

---

### Post by Whiffle on 2008-05-09
```

[andy@whiffle:~]$ lsmod | grep usb                                                          (05-09 13:18)
usb_storage            83648  1
usbhid                 42560  0
hid                    38272  1 usbhid
ff_memless              5128  1 usbhid
usbcore               128620  5 usb_storage,usbhid,ehci_hcd,ohci_hcd

```

Hmmm, not quite  the same (this is on arch though, kernel  2.6.24).  I wonder what scsi_mod and libusual do.    I guess you could experiment by adding scsi_mod to /etc/modprobe.d/blacklist  and then rebooting.  I really don't know what else to tell you right now.

---

### Post by buggs187 on 2008-05-09
Here's what I have loaded
```
usb_storage            73664  1 
libusual               19108  1 usb_storage
usbhid                 31872  0 
hid                    38784  1 usbhid
usbcore               146028  5 usb_storage,libusual,usbhid,ohci_hcd
scsi_mod              151436  5 usb_storage,sg,sr_mod,sd_mod,libata

```

---

### Post by fusionisthefuture on 2008-05-17
im having this same problem, i get about 2.5 mbyte/sec when uploading to a usb 2.0 hd on a usb 2.0 port. (hp pavillion dv2200 cto notebook)

---

### Post by buggs187 on 2008-05-17
OK I might have found something... 
When I first insert any USb device I have to run the command or the device is not detected.
```
sudo rmmod ehci_hcd
```
Which from my understanding removes USB 2.0 support from the Kernal?

After that command if I run
```
sudo modprobe ehci_hcd
```
I can tranfer files at a normal speed of about 18mb/s compaired to the 900kb/s that I was recieving before.

So my question is. Is there a way to automate this process? Should I just create a script that loads with Ubuntu?

---

### Post by fusionisthefuture on 2008-05-17
i have to issue no such command, it automatically detects and mounts the hd, but the rates are slow.  i also dont know how to do startup scripts.

---

### Post by Zularan on 2008-05-21
Think I've solved this.  Seems we need to load the 'ehci_hcd' module to take advantage of USB2 speeds.  ```
sudo modprobe ehci_hcd
``` will load the module and to do this automatically on boot we just add 'ehci_hcd' to the modules file (as root)
```
sudo gedit /etc/modules
```
and add 
```
ehci_hcd
```
to the list.  After I got this module running I went from 500k/s to over 12meg/s.

---

### Post by buggs187 on 2008-05-28
Ok so i have added this to see if it works and have come up empty handed. If I have a USB2.0 device connected and powered on during boot up this works but thats it. I have also found another problem now. If I have a External Hard Drive connected and leave it idle for a few minutes (2-3) it stops working. I have to ```
sudo rmmod ehci_hcd 
```
to re-enable the device with USB1.0 then ```
sudo modprobe ehci_hcd
``` for USB2.0
Not sure what causes this. It's not too frustrating to do this but I should not have too. But then again Ubuntu is free and it beats getting bent over by Microshit ...

---

### Post by Kernel_Krunch on 2008-06-05
Try this

```
echo 1024 > /sys/block/sd*/device/max_sectors
```

change sd* to your drive.

if your drive has 2MB buffer then try the value 2048 but 1024 should be fine.

hope it helps

---

### Post by Roostey on 2008-06-09
I've got the same slow file copy problem as described here - fast initially, then it slows to a crawl.  I've got a Compaq V3118AU

My original bug report was merged with this one [here]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/197762")

Only a few people seem to have reported this problem.  I suspect it affects a lot more, but they haven't noticed it yet because it's not an issue for small files.

It's certainly driving me mad.  I have to boot a Desktop CD of Feisty to be able to back up my home partition!  In my case the copy bug also affects network file transfers, so my file sever is all but useless (DNS-323 mounted with UFS).  I'd go back to Feisty permanently but I need the latest versions of a couple of apps.

I tried the ehci_hcd tip, but it didn't help much for my situation, though I did get some bizarre behaviour.  The USB drive I'm using isn't particularly fast (~9MB/s write speed) and after using this tip, file copies start off well in excess of the maximum write speed of the drive, up to 18MB/s (never seen it go this high before), then after about 200MB the copying stalled then tailed off to about 2MB/s, which is at least a little better than the sub 1MB/s speed I'm used to.
 
Sometimes my system will slow to a crawl during a file copy.  When this has happened, I've opened the the system monitor and neither CPU core is over 20%, yet the GUI is sluggish and unresponsive.  This happens maybe 5% of the time.

---

### Post by cubeist on 2008-06-15
This is also happening to me.  I didn't really notice until I tried backing up a few gigs and I was getting about 500KB/s!  Now that I am aware of it it appears the transfers start at a normal usb2.0 speed and then drop down and crawl along.  The module add-in trick does nothing for me.

I am on a Desktop system, gutsy was working aok.  I have a similar lsmod as other posts here...
$ lsmod | grep usb
usb_storage            82496  0 
libusual               23520  1 usb_storage
usbhid                 35296  0 
hid                    44992  1 usbhid
lmpcm_usb               8192  0 
usbcore               169904  7 usb_storage,libusual,usbhid,lmpcm_usb,ohci_hcd,ehci_hcd
scsi_mod              178488  6 usb_storage,sbp2,sr_mod,sg,sd_mod,libata


This is very frustrating now that I am aware of it!

Edit - Doh!
Fixed it.  I can't believe I didn't try this earlier, but the port I was using was only USB1.1 not USB2.0, so I plugged it in to the back of the computer and voila! Full USB speed.  Maybe this is what is happening to others?

---

### Post by Roostey on 2008-07-24
I've found a solution that works on my systems.  I added pci=routeirq to my boot options for grub and I got back full USB and network speed.

---

### Post by Roostey on 2008-07-24
> **Roostey said:**
> I've found a solution that works on my systems.  I added pci=routeirq to my boot options for grub and I got back full USB and network speed.


I've detailed how to do it [here]("http://ubuntuforums.org/showpost.php?p=5447719&postcount=10")

---

