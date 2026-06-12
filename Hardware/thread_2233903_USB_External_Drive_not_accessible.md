---
title: "USB External Drive not accessible"
date: 2014-07-11
forum: Hardware
---

### Post by NertSkull on 2014-07-11
I have a USB 3 drive (WD My Passport) that has worked for ages on my computer.  But now when I plug it in, I can't open it up.  It is not recognized in fdisk at all.

It still works on USB 2 ports.  Just not my USB 3 ports.

All my other external drives and flash drives (which are all USB 3 drives) work in the same (in all) USB 3 ports.  I even have another WD MyPassport (same type) that still works.  Its just this one drive.

I don't think its the drive itself though.  Because like I said, it still works in the USB 2 ports on my linux computer.  And it works on all USB ports (USB 2 and 3) and any of the other computers here at work.  The drive works fine everywhere except my USB 3 ports.  But like I said, my USB 3 ports work fine with any other drive.

The drive is kind of recognized, here is dmesg after plugging it in.  But fdisk doesn't recognize it at all.

```
[ 1660.590184] usb 6-1.4: new SuperSpeed USB device number 7 using xhci_hcd[ 1660.609863] scsi11 : usb-storage 6-1.4:1.0
[ 1661.609629] scsi 11:0:0:0: Direct-Access     WD       My Passport 0748 1019 PQ: 0 ANSI: 6
[ 1661.609900] scsi 11:0:0:1: Enclosure         WD       SES Device       1019 PQ: 0 ANSI: 6
[ 1661.610679] sd 11:0:0:0: Attached scsi generic sg5 type 0
[ 1661.610784] ses 11:0:0:1: Attached Enclosure device
[ 1661.610848] ses 11:0:0:1: Attached scsi generic sg6 type 13



```

So it appears to at least see the drive.  

Why doesn't fdisk recognize it?

I don't believe I did any sort of updating between the drive working and not working (I'm not 100% positive on that,  I just don't remember running updates recently, and I use this drive multiple times every day, but I may just be forgetful about the last time I ran updates).

How do I get access to this drive on my USB 3 ports?  

Thanks!

---

### Post by NertSkull on 2014-07-16
I hate to bump a thread, but it has been 4 days and I still have the same problem.  Hard drive works everywhere but my USB 3 ports.  All other drives work in my USB 3 ports.

---

### Post by jeremy31 on 2014-07-16
Are the other drives Western Digital also?

The WD I have is the only one that causes problems

---

### Post by NertSkull on 2014-07-16
I have a 1TB WD MyPassport that works fine in the ports.  But I have a 2TB WD MyPassport which is the one that causes problems.  

I then have a Corsair Voyager Go USB 3 flash drive that works fine everywhere.  And I have a multitude of USB 2 flash drives that also work fine everywhere.

---

### Post by NertSkull on 2014-07-23
So this still is a problem, but it has grown.  Now BOTH my WD MyPassport drives don't recognize in USB 3.  But both still recognize in USB 2.

I got told to try check disk in windows (since they are ntfs drives, which I have to have since most work computers are Win7).

I tried check disk 3 or 4 times, with reboots between on the drives.  Always came back fine.

SO...I tried changing the drives to ext4.  I formatted the 2TB one to ext 4.  It STILL doesn't work on USB 3.  As an ext4 drive, it still works as a USB 2.  The ext4 format (just like the ntfs format) works on my home USB 3.0 linux (both my home and work computer are kubuntu 12.04).

So even as ext4, I have the same problem.  Just these two drives don't work on my work computer usb 3.0.  The drives work on usb 3 on other computers.  The drives work on usb 2 on this computer.

Other usb 3 drives work fine on my work computer.

I have to figure this out.  I am routinely transferring 400-900 Gb at work 1-2 times a week.  Last night it took 11 hours to transfer my data on usb 2.  

I really don't want to have to buy a new drive right now.  But this is no good.

---

### Post by NertSkull on 2014-07-25
Eventually someone will see this that knows enough about hard drives to at least point me in the right direction.

Here is one more piece of information.  I discovered if I leave the drives plugged in while I boot, the boot hangs and I can see the following error:

```
ata_id[834]: HDIO_GET_IDENTITY failed for /dev/sde: Invalid argument
```

I tried looking up that error, and I got no where.  Either it was an upgrade issue (which is not the case for me).  Or I found things saying "just ignore the error, its a hdparm issue and not important". 

Anyone?

---

### Post by NertSkull on 2014-07-28
Bump...sorry.

---

### Post by NertSkull on 2014-07-28
So I tried a few more drives from co-workers, just to make sure.  I tried a 3rd WD MyPassport, it did NOT work.  I tried a Silicone Power drive, it did NOT work.  I tried a Toshiba drive, it DID work.  I tried another flash usb 3.0 drive and it DID work.  And I tried a seagate drive, it did NOT work.

So I'm down to no ideas.  All flash drives I've tried have worked.  But right now, only the Toshiba external USB 3 HDD works on my ports.  

All of these HDD drives and flash drives work on other USB 3 ports on other computers.

All of them worked on my machine just a few weeks (maybe a month or two) ago.

---

### Post by NertSkull on 2014-07-29
One more piece of information.  I forgot I had a dual-boot windows install on this computer.  It's been like a year since I've used it, but I have it.

And....The hard drives work fine there.  All hard drives work in my USB 3 ports in windows.

So it HAS to be a setting in linux/ubuntu here that is causing me grief.  I REALLY don't want to re-install.  But after 2+ weeks here of no answers, I may just have to.  But I thought I would try again, in case someone out there has any brilliant ideas.

---

### Post by NertSkull on 2014-08-01
Bump, I'm going to try this a few more times.

---

### Post by NertSkull on 2014-08-07
Trying again.

---

