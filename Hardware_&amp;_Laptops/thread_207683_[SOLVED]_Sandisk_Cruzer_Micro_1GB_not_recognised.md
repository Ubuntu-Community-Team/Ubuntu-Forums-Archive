---
title: "[SOLVED] Sandisk Cruzer Micro 1GB not recognised"
date: 2006-07-02
forum: Hardware &amp; Laptops
---

### Post by gwi on 2006-07-02
If I plugin my Sandisk Cruzer Micro 1GB (type SDCZ6-1024), it is not properly recognised. The led on the Cruzer lights up for a few seconds, but that's it. My old USB memory (Apacer HandyDrive 64MB USB1.1) is working. The Cruzer is recognised in Windows XP (on the same dual-boot pc).

What is the problem here?

Some output that might help diagnosing:

dmesg:
```

[  824.985348] usb 2-7: new high speed USB device using ehci_hcd and address 13
[  827.549481] usb 2-7: unable to read config index 0 descriptor/all
[  827.549486] usb 2-7: can't read configurations, error -110
[  827.605382] usb 2-7: new high speed USB device using ehci_hcd and address 14
[  830.172159] scsi6 : SCSI emulation for USB Mass Storage devices
[  830.172232] usb-storage: device found at 14
[  830.172234] usb-storage: waiting for device to settle before scanning
[  832.672829]   Vendor: SanDisk   Model: U3 Cruzer Micro   Rev: 2.15
[  832.672838]   Type:   Direct-Access                      ANSI SCSI revision: 02
[  850.282458] usb 2-7: can't restore configuration #1 (error=-110)
[  850.282475] usb 2-7: USB disconnect, address 14
[  850.282513] sd 6:0:0:0: scsi: Device offlined - not ready after error recovery
[  850.282531] sd 6:0:0:0: rejecting I/O to offline device
[  850.282537] sd 6:0:0:0: rejecting I/O to offline device
[  850.282541] sd 6:0:0:0: rejecting I/O to offline device
[  850.282545] sdb : READ CAPACITY failed.
[  850.282547] sdb : status=0, message=00, host=1, driver=00
[  850.282549] sdb : sense not available.
[  850.282552] sd 6:0:0:0: rejecting I/O to offline device
[  850.282556] sdb: Write Protect is off
[  850.282558] sdb: Mode Sense: 00 00 00 00
[  850.282559] sdb: assuming drive cache: write through
[  850.282594] sd 6:0:0:0: Attached scsi removable disk sdb
[  850.282628] sd 6:0:0:0: Attached scsi generic sg1 type 0
[  850.288431] usb-storage: device scan complete
[  850.344388] usb 2-7: new high speed USB device using ehci_hcd and address 15
[  852.908516] usb 2-7: unable to read config index 0 descriptor/all
[  852.908521] usb 2-7: can't read configurations, error -110
[  852.964420] usb 2-7: new high speed USB device using ehci_hcd and address 16
[  855.528517] usb 2-7: unable to read config index 0 descriptor/all
[  855.528522] usb 2-7: can't read configurations, error -110
[  855.584456] usb 2-7: new high speed USB device using ehci_hcd and address 17
[  858.094660] usb 2-7: can't set config #1, error -110
[  858.154576] usb 2-7: new high speed USB device using ehci_hcd and address 18
[  860.666799] usb 2-7: can't set config #1, error -110

```

tail -f /var/log/messages:
```

Jul  2 14:34:41 saturnus kernel: [  850.282513] sd 6:0:0:0: scsi: Device offlined - not ready after error recovery
Jul  2 14:34:41 saturnus kernel: [  850.282545] sdb : READ CAPACITY failed.
Jul  2 14:34:41 saturnus kernel: [  850.282547] sdb : status=0, message=00, host=1, driver=00
Jul  2 14:34:41 saturnus kernel: [  850.282549] sdb : sense not available.
Jul  2 14:34:41 saturnus kernel: [  850.282556] sdb: Write Protect is off
Jul  2 14:34:41 saturnus kernel: [  850.282594] sd 6:0:0:0: Attached scsi removable disk sdb
Jul  2 14:34:41 saturnus kernel: [  850.282628] sd 6:0:0:0: Attached scsi generic sg1 type 0
Jul  2 14:34:41 saturnus kernel: [  850.344388] usb 2-7: new high speed USB device using ehci_hcd and address 15
Jul  2 14:34:46 saturnus kernel: [  852.964420] usb 2-7: new high speed USB device using ehci_hcd and address 16
Jul  2 14:34:51 saturnus kernel: [  855.584456] usb 2-7: new high speed USB device using ehci_hcd and address 17
Jul  2 14:34:57 saturnus kernel: [  858.154576] usb 2-7: new high speed USB device using ehci_hcd and address 18

```

lsusb:
```

Bus 002 Device 001: ID 0000:0000
Bus 001 Device 002: ID 056a:0010 Wacom Co., Ltd Graphire
Bus 001 Device 003: ID 056d:0002 EIZO Corp.
Bus 001 Device 001: ID 0000:0000

```

---

### Post by Bloch on 2006-07-02
No solution, just a comment.
I had that same 1GB Sandisk. After several weeks of use between ubuntu and windows xp the device became corrupted. I could not reformat it. The system wouyld begin to transfer files to the device and then freeze. I would be unable to umount the device or terminate the transfer.

I see that the Sandisk is recognised by your system. I can only suggest that the filesystem has become corrupted.
I remember that when I had problems I googled "Sandisk problems" and it appears the device is not as reliable as other memory sticks. However the company may have improved the model since.

Try formatting it on windows and see if that helps.

---

### Post by gwi on 2006-07-04
When I plug the Cruzer in on Windows, it creates a removeable drive, and a CDROM drive with some U3 software on it.
I already formatted it on Windows, just to see if I could get rid of the additional CDROM (it didn't, so it is probably in the stick's firmware).

I tried it on another computer, running Ubuntu (2.6.15-25-686). No problem.
At home I am using 2.6.15-25-amd64-k8. Could that be an issue?

---

### Post by Mateo on 2006-07-04
Sorry I can't help, just a comment.  i also have a 1GB Cruzer Micro and have never had a problem.  Mine is about 1 years old.  However I have only used ubuntu for about 1 1/2 weeks.  Before that I used Fedora (also with GNOME) and had no problems there.  Just saying that this problem should be fixable, i believe.

---

### Post by Happy Dave on 2006-07-04
I'm having almost the same issue.  I've got the same USB stick, recognised fine in windows XP.  I was happily transferring files back and forth, but when I upgraded to Dapper from Breezy, it no longer opens the stick.  It can see it and knows it's a Sandisk, but no dice on actually opening it.  It's not super-essential as I use the Ubuntu machine as a standalone writing machine, but it's a pain.

Any ideas?

To reiterate, the stick opens fine in XP, but can't be mounted under Ubuntu Dapper, despite working fine (automatically even) in Breezy.

---

### Post by Bloch on 2006-07-05
> When I plug the Cruzer in on Windows, it creates a removeable drive, and a CDROM drive with some U3 software on it.
I already formatted it on Windows, just to see if I could get rid of the additional CDROM (it didn't, so it is probably in the stick's firmware).

This is the problem I had. I believe it may have started when I transferred an iso file. Windows seemed to think it was a CD-rom.

I download windows progs that claim to rescue memory stick problems but nothing worked. I brought it back to the shop. A search of reviews etc indicates the 1GB Cruzer, or at least some lines of the product, are not reliable.

gwi, you say it is recognized on windows xp, but is it working properly there?

---

### Post by gwi on 2006-07-05
Under Windows XP it is working properly.

As I said earlier: it is also working properly on a 686-version of Ubuntu 6.06.
It is just the k8-version where I experience these problems.

Edit: yesterday tried it: it worked. Still don't know if this was an exception, or if the behaviour of the past days was.
Could there be a timimg issue?

---

### Post by streakeagle on 2006-07-08
Spread the word: if you have a Sandisk U3 Cruzer that isn't recognized properly by Windows, the problem is a conflict between U3 and some other CD/DVD burning application on your PC. 

Go to [http://www.U3.com](http://www.U3.com) for support. I didn't even bother with uninstalling NERO to test their theory. I went to: [http://www.u3.com/uninstall/](http://www.u3.com/uninstall/) then downloaded and ran the U3 uninstall exe (on a pc that worked with the U3 Cruzer). Now I have a single 1GB drive instead of a 6MB CD and <1GB drive. Sure the U3 promises a lot of great things, but I needed a USB key that works on any PC, not a portable user preferences/email documents folder. I am much happier now :)

---

### Post by gwi on 2006-07-09
> **streakeagle said:**
> Spread the word: if you have a Sandisk U3 Cruzer that isn't recognized properly by Windows, the problem is a conflict between U3 and some other CD/DVD burning application on your PC.
My Cruzer is recognised by Windows, it's Ubuntu that doesn't.

> **streakeagle said:**
> Go to [http://www.U3.com](http://www.U3.com) for support. I didn't even bother with uninstalling NERO to test their theory. I went to: [http://www.u3.com/uninstall/](http://www.u3.com/uninstall/) then downloaded and ran the U3 uninstall exe (on a pc that worked with the U3 Cruzer). Now I have a single 1GB drive instead of a 6MB CD and <1GB drive. Sure the U3 promises a lot of great things, but I needed a USB key that works on any PC, not a portable user preferences/email documents folder. I am much happier now :)
I am not: the U3 uninstall program does not recognise the Cruzer (and yes, I know the uninstaller is a Windows program, ran it under Windows XP Pro SP2).

In the meantime I tested the Cruzer on Ubuntu 6.06 amd64-generic: same result as with amd64-k8: not recognised when plugging into a running system, hangs on black screen when booting with the stick plugged in.
Maybe I will try the i386 version to see what happens there.

---

### Post by gwi on 2006-07-14
Well, I finally got rid of the U3 crap. On another computer the uninstaller did work. It didn't change the results though. Yesterday I read that fdisk can be used on USB flash drives. (Maybe I could have removed the U3 that way!) I removed the existing partition, and created a new one, and formatted it as FAT32 (mkfs.vfat -F 32). All done in Linux, but still not recognised on a 64-bit kernel.

I booted the AMD64 live cd: the USB flash drive was not recognised.
I booted the installed AMD64-k8 kernel: the USB flash drive was not recognised.
I booted the i386 live cd: the USB flash drive worked properly.

So it seems only the 64-bit kernels have a problem. I have tried dozens of times, but the flash drive was only (partly) recognised two or three times. Is this a timing problem?

When I plug in the drive and do a lsusb or cat /proc/bus/usb/devices, nothing happens. The shell does nothing, no prompt. It just echoes what I type. Ctrl-C or ctrl-D don't work. Alt-F4 does close the window, but that's it.

lspci shows (among others):
0000:00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
0000:00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)

tail -f /var/log/syslog showed nothing when plugging in the flash drive.

Almost looks like the USB system has stopped running, but my USB connected Wacom Graphire still works.

Any ideas what is going on here? My motherboard is an Asus A8N SLI DeLuxe (nForce4 chipset), with an Athlon64-3200+ and 3GB RAM.
Did someone experience the same problems?

---

### Post by Merkwurdigliebe on 2006-11-09
Yes, I have exactly the same problem, but will all types of USB disks.

I can't get the 64-bit version of 6.10 to mount them on this A8N SLI 3500+ 3 GB board either.

They worked fine on the same board with the 32-bit version.  The drives work fine in Windows XP 64 on the same box.  They work fine on an ABIT k8 AMD 64 board as well.  T

I've tried 3 drives.  They are fine.  I can take them to another AMD 64 machine (NVidia chipset, too) running a 6.10 64-bit install, and they are fine there.  I am getting access to them over the network right now. 

The 2.6.17-10-generic kernel is broken for this board with this amount of RAM.

---

### Post by Merkwurdigliebe on 2006-11-09
Had to add this:

On the same machine, the Centos 4.4 64-bit install has no problems accessing the drives.

Anyone solved this yet?

---

### Post by Spenser_Gilliland on 2006-11-09
i got the 2gb version.  The funny thing is on there packaging they say that it supports Linux. lol.

---

### Post by webs05 on 2007-02-01
Just at work I had someone bring a 1gb Sandisk Cruzer Micro with that U3 crap on it.  And doesn't matter what we did to it, we couldn't fully remove that stuff and get a fully functioning USB drive.  Bottom line, no one at this college will be buying one of those drives, a few of us here are bloggers, and will be mentioning this.  And we will likely place a call to Sandisk about it.

We don't ask for much, but when someone buys a USB drive with their own dough, it should be theirs to use freely.  I hope I do get the chance to work on one of these, so I can come up with a solution, but for now F*** Sandisk.

---

### Post by webs05 on 2007-02-01
Sorry for the Double dip, but I just found out some more info.  Any drive with the U3 technology is going to have this problem.  And you have to be an administrator to remove the U3 stuff.  Problem is none of our 300 some users are admins for obvious reasons.  

So when we admins lon in to remove the U3 we have now accessed the drive with our account.  Once the U3 is removed and the drive is normal again the other users cannot access the drive.  Because apparently when you access the drive with one account, that is the only account you can use to access the drive.  At least in a Windows environment.

And there still seems no way to nuke the drive in Linux to make it fully funtional.  In fact, I believe you have to flash the rom chip in it to be able to do anything.

Damn U3:mad: :mad:

---

### Post by Gbagar on 2007-09-26
Hello there, this is not an answer to your question. I have the same problem now. but the diffrence is that my drive is 512 but the same Sandisk Cruzer Micro!!! 

can any body help now!!!

:confused:

---

### Post by objem on 2007-10-03
I finally got a 1 gig Cruzer to work. When it first didn't work in Feisty 64 bit I thought it was the U3 software, So I removed it with a windows program from [www.u3.com/uninstall/](www.u3.com/uninstall/)

Still wasn't working, so I looked at the system logs when I did a lsusb. Turns out the ehci_hcd driver wasn't accepting an address.

Got it working by reloading the driver: 
sudo modprobe -r ehci_hcd

Showed up straight away in the file browser. Don't know if you have to do this every time though.

---

### Post by borovy3488 on 2007-10-03
I had the 2 GB version and I was having the same problem. All I had to do was plug it back into a windows PC and take off the password protection.  Plugged it in, and it worked perfect.

---

### Post by poe503 on 2007-10-03
The uninstall program worked fine in XP to remove that U3 business tho the uninstaller complained that it couldn't finish the job.  I got the full 1gb.  In plain old Unbuntu 7.04, it is recognized and works like a charm.  I might advise left clicking the icon and toggling 'eject' before removing the usb chip to avoid corrupting files, same applies to Wind'ohs.

---

### Post by nealos on 2008-07-09
I had this problem with the cruzer 1gb after upgrading to 8.04.  Installing pmount from synaptic solved the problem (hal was already installed by default).

nealos

Dell Dimension 4300
Ubuntu 8.04

---

