---
title: "External USB Hard Drive Woes"
date: 2006-05-31
forum: Hardware &amp; Laptops
---

### Post by ScatterBrain on 2006-05-31
I'm not entirely sure that this is a specific laptop problem, but I'm experiencing it on a laptop, so here I go...

I've got a Dell Inspiron 6000d.  The external Hard Drive in question is an 80GB Western Digitial Scorpio 2.5" laptop hard drive in a Silvestone USB 2.0 external enclosure. 

In Windows, this setup works fine - I can even boot off of the USB drive if I choose to (the external drive came from a laptop hard drive upgrade project a couple of weeks back and still WinXP on it.).

When I fire up Dapper and plug in the drive, I get this in **/var/log/syslog**:

```
May 31 21:32:35 enterprise kernel: [4298016.679000] usb 5-8: new high speed USB device using ehci_hcd and address 6
May 31 21:32:39 enterprise kernel: [4298020.583000] usb 5-8: device not accepting address 6, error -32
May 31 21:32:40 enterprise kernel: [4298020.702000] usb 5-8: new high speed USB device using ehci_hcd and address 7
May 31 21:32:40 enterprise NetworkManager: <debug info>^I[1149125560.423251] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ed06_4500_1966051022645658').
May 31 21:32:40 enterprise NetworkManager: <debug info>^I[1149125560.456566] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ed06_4500_1966051022645658_if0').
May 31 21:32:40 enterprise kernel: [4298021.083000] scsi5 : SCSI emulation for USB Mass Storage devices
May 31 21:32:40 enterprise kernel: [4298021.083000] usb-storage: device found at 7
May 31 21:32:40 enterprise kernel: [4298021.083000] usb-storage: waiting for device to settle before scanning
May 31 21:32:40 enterprise NetworkManager: <debug info>^I[1149125560.583294] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ed06_4500_1966051022645658_if0_scsi_host').
May 31 21:32:40 enterprise NetworkManager: <debug info>^I[1149125560.654404] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ed06_4500_1966051022645658_usbraw').
May 31 21:32:45 enterprise kernel: [4298026.314000]   Vendor: WDC WD80  Model: 0VE-75HDT1        Rev: 11.0
May 31 21:32:45 enterprise kernel: [4298026.314000]   Type:   Direct-Access                  ANSI SCSI revision: 00
May 31 21:32:45 enterprise kernel: [4298026.316000] SCSI device sdb: 156301489 512-byte hdwr sectors (80026 MB)
May 31 21:32:45 enterprise kernel: [4298026.316000] sdb: assuming drive cache: write through
May 31 21:32:45 enterprise kernel: [4298026.317000] SCSI device sdb: 156301489 512-byte hdwr sectors (80026 MB)
May 31 21:32:45 enterprise kernel: [4298026.317000] sdb: assuming drive cache: write through
May 31 21:32:45 enterprise kernel: [4298026.317000]  sdb: sdb1
May 31 21:32:45 enterprise kernel: [4298026.617000] sd 5:0:0:0: Attached scsi disk sdb
May 31 21:32:45 enterprise kernel: [4298026.617000] sd 5:0:0:0: Attached scsi generic sg2 type 0
May 31 21:32:45 enterprise kernel: [4298026.619000] usb-storage: device scan complete
May 31 21:32:45 enterprise NetworkManager: <debug info>^I[1149125565.962624] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ed06_4500_1966051022645658_if0_scsi_host_scsi_device_lun0').
May 31 21:32:46 enterprise NetworkManager: <debug info>^I[1149125566.043847] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_ed06_4500_1966051022645658_if0_scsi_host_scsi_device_lun0_scsi_generic').

``` 

So far so good - the thing is recognized and all's well.  Except that I can't mount the drive.  ](*,)    After a few seconds, I start to get these messages in the syslog:

```
May 31 21:33:16 enterprise kernel: [4298056.874000] usb 5-8: reset high speed USB device using ehci_hcd and address 7
May 31 21:33:26 enterprise kernel: [4298067.304000] usb 5-8: device not accepting address 7, error -110
May 31 21:33:26 enterprise kernel: [4298067.406000] usb 5-8: reset high speed USB device using ehci_hcd and address 7
May 31 21:33:37 enterprise kernel: [4298077.840000] usb 5-8: device not accepting address 7, error -110
May 31 21:33:37 enterprise kernel: [4298077.969000] usb 5-8: reset high speed USB device using ehci_hcd and address 7
May 31 21:33:40 enterprise kernel: [4298081.120000] usb 5-8: device descriptor read/64, error -110
May 31 21:33:55 enterprise kernel: [4298096.334000] usb 5-8: device descriptor read/64, error -110
May 31 21:33:55 enterprise kernel: [4298096.542000] usb 5-8: reset high speed USB device using ehci_hcd and address 7
May 31 21:33:58 enterprise kernel: [4298099.663000] usb 5-8: device descriptor read/64, error -110
May 31 21:34:14 enterprise kernel: [4298114.896000] usb 5-8: device descriptor read/64, error -110
May 31 21:34:14 enterprise NetworkManager: <debug info>^I[1149125654.325402] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ed06_4500_1966051022645658_if0_scsi_host_scsi_device_lun0_scsi_generic').
May 31 21:34:14 enterprise NetworkManager: <debug info>^I[1149125654.330170] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ed06_4500_1966051022645658_if0_scsi_host_scsi_device_lun0').
May 31 21:34:14 enterprise NetworkManager: <debug info>^I[1149125654.333671] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ed06_4500_1966051022645658_if0_scsi_host').
May 31 21:34:14 enterprise NetworkManager: <debug info>^I[1149125654.337021] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ed06_4500_1966051022645658_if0').
May 31 21:34:14 enterprise NetworkManager: <debug info>^I[1149125654.340350] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ed06_4500_1966051022645658').
May 31 21:34:14 enterprise kernel: [4298115.012000] usb 5-8: USB disconnect, address 7
May 31 21:34:14 enterprise kernel: [4298115.012000]  5:0:0:0: scsi: Device offlined - not ready after error recovery
May 31 21:34:14 enterprise kernel: [4298115.016000]  5:0:0:0: SCSI error: return code = 0x10000
May 31 21:34:14 enterprise kernel: [4298115.016000] end_request: I/O error, dev sdb, sector 156301488
May 31 21:34:14 enterprise kernel: [4298115.016000] printk: 482 messages suppressed.
May 31 21:34:14 enterprise kernel: [4298115.016000] Buffer I/O error on device sdb, logical block 156301488
May 31 21:34:14 enterprise kernel: [4298115.038000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise kernel: [4298115.038000] Buffer I/O error on device sdb, logical block 156301488
May 31 21:34:14 enterprise kernel: [4298115.039000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise kernel: [4298115.039000] Buffer I/O error on device sdb, logical block 156301488
May 31 21:34:14 enterprise kernel: [4298115.039000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise kernel: [4298115.039000] Buffer I/O error on device sdb, logical block 156301488
May 31 21:34:14 enterprise kernel: [4298115.040000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise kernel: [4298115.040000] Buffer I/O error on device sdb, logical block 156301424
May 31 21:34:14 enterprise kernel: [4298115.040000] Buffer I/O error on device sdb, logical block 156301425
May 31 21:34:14 enterprise kernel: [4298115.040000] Buffer I/O error on device sdb, logical block 156301426
May 31 21:34:14 enterprise kernel: [4298115.040000] Buffer I/O error on device sdb, logical block 156301427
May 31 21:34:14 enterprise kernel: [4298115.040000] Buffer I/O error on device sdb, logical block 156301428
May 31 21:34:14 enterprise kernel: [4298115.040000] Buffer I/O error on device sdb, logical block 156301429
May 31 21:34:14 enterprise kernel: [4298115.042000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise last message repeated 3 times
May 31 21:34:14 enterprise kernel: [4298115.043000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise last message repeated 2 times
May 31 21:34:14 enterprise kernel: [4298115.044000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise last message repeated 2 times
May 31 21:34:14 enterprise kernel: [4298115.045000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise last message repeated 2 times
May 31 21:34:14 enterprise kernel: [4298115.047000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise last message repeated 2 times
May 31 21:34:14 enterprise kernel: [4298115.048000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise last message repeated 3 times
May 31 21:34:14 enterprise kernel: [4298115.049000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise last message repeated 4 times
May 31 21:34:14 enterprise kernel: [4298115.050000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise last message repeated 3 times
May 31 21:34:14 enterprise kernel: [4298115.051000]  5:0:0:0: rejecting I/O to dead device
May 31 21:34:14 enterprise NetworkManager: <debug info>^I[1149125654.385322] nm_hal_device_removed (): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_ed06_4500_1966051022645658_usbraw').
May 31 21:34:14 enterprise kernel: [4298115.123000] usb 5-8: new high speed USB device using ehci_hcd and address 8
May 31 21:34:24 enterprise kernel: [4298125.530000] usb 5-8: device not accepting address 8, error -110
May 31 21:34:24 enterprise kernel: [4298125.675000] usb 5-8: new high speed USB device using ehci_hcd and address 9
May 31 21:34:35 enterprise kernel: [4298136.102000] usb 5-8: device not accepting address 9, error -110
May 31 21:34:35 enterprise kernel: [4298136.225000] usb 5-8: new high speed USB device using ehci_hcd and address 10
May 31 21:34:38 enterprise kernel: [4298139.333000] usb 5-8: device descriptor read/64, error -110

``` 

This second batch of errors repeats over and over until I unplug the drive.  I've done some Googling and tried a few things, none of which has worked.:( 

I'm hoping this has happened to in the past and is willing to help me solve it.  

It's not life-threatening that I use the external USB drive, it would just make things a lot easier for me.

---

### Post by skyshark88 on 2006-05-31
Dude, what are you trying to do to it...
 Really you have a bootable, portable OS..
Im not a windows fan at all but man I can't get anything to do that linux as well..

---

### Post by skyshark88 on 2006-05-31
Must be the windows MBR or the fact  you have no linux partitions, get copy of ultimate boot disk and resize the xp and create a fat32 partition so you could read it from xp and linux..

---

### Post by K.Mandla on 2006-05-31
I'm a little confused: Are you booting off an internal drive with Dapper installed, and then plugging in an external that has a Dapper installation on it as well?

---

### Post by ScatterBrain on 2006-06-01
OK folks, I'm NOT trying to boot off the USB drive - I was just pointing that out because the drive has a fully-functional copy of Windows on it, and my laptop supports booting from USB devices, ***I could do it if I wanted to***.  In fact I have on at least one occasion.

What I'm trying to do is simply use the drive as another storage device.  There is a large chuck of the drive (50 GB+) that is sitting un-partitioned.  My goal is to use at least that portion of the drive as additional space for portable needs.  Backups, large file transfers...that sort of thing.

At this moment, I can't use fdisk, cfdisk or even mount the existing NTFS partition.  The drive simply fails to show up when I plug it up - spewing all the errors listed above.  I know that the drive and enclosure are fine, because when I plug them into a Windows machine, the drive is recognized, I can see the NTFS drive and the files it contains and I can even create additional Windows partitions if need be.

Have I made my problem clear as mud now?  Sorry for the confusion.

---

### Post by ScatterBrain on 2006-06-01
Additional information...

I've got a thumb-drive - a Lexar 512MB Jumbdrive Sport.  When I plug it into the laptop, it works as expected.  I even get a nautilus window showing the contents of the drive after it's automounted.

Just in case it matters, here's a snippet from[COLOR=Green]** /var/log/syslog**[/COLOR] after the drive is plugged in:

```
Jun  1 11:13:13 enterprise kernel: [4295240.127000] usb 5-7: new high speed USB device using ehci_hcd and address 3
Jun  1 11:13:14 enterprise kernel: [4295240.427000] Initializing USB Mass Storage driver...
Jun  1 11:13:14 enterprise kernel: [4295240.428000] scsi2 : SCSI emulation for USB Mass Storage devices
Jun  1 11:13:14 enterprise kernel: [4295240.429000] usb-storage: device found at 3
Jun  1 11:13:14 enterprise kernel: [4295240.429000] usb-storage: waiting for device to settle before scanning
Jun  1 11:13:14 enterprise kernel: [4295240.429000] usbcore: registered new driver usb-storage
Jun  1 11:13:14 enterprise kernel: [4295240.429000] USB Mass Storage support registered.
Jun  1 11:13:18 enterprise kernel: [4295245.445000]   Vendor: LEXAR     Model: JUMPDRIVE SPORT   Rev: 1000
Jun  1 11:13:18 enterprise kernel: [4295245.445000]   Type:   Direct-Access                  ANSI SCSI revision: 00
Jun  1 11:13:18 enterprise kernel: [4295245.447000] SCSI device sdb: 1014784 512-byte hdwr sectors (520 MB)
Jun  1 11:13:18 enterprise kernel: [4295245.448000] sdb: Write Protect is off
Jun  1 11:13:18 enterprise kernel: [4295245.448000] sdb: Mode Sense: 43 00 00 00Jun  1 11:13:18 enterprise kernel: [4295245.448000] sdb: assuming drive cache: write through
Jun  1 11:13:18 enterprise kernel: [4295245.450000] SCSI device sdb: 1014784 512-byte hdwr sectors (520 MB)
Jun  1 11:13:18 enterprise kernel: [4295245.452000] sdb: Write Protect is off
Jun  1 11:13:18 enterprise kernel: [4295245.452000] sdb: Mode Sense: 43 00 00 00Jun  1 11:13:18 enterprise kernel: [4295245.452000] sdb: assuming drive cache: write through
Jun  1 11:13:19 enterprise kernel: [4295245.452000]  sdb: sdb1
Jun  1 11:13:19 enterprise kernel: [4295245.523000] sd 2:0:0:0: Attached scsi removable disk sdb
Jun  1 11:13:19 enterprise kernel: [4295245.523000] sd 2:0:0:0: Attached scsi generic sg2 type 0
Jun  1 11:13:19 enterprise kernel: [4295245.524000] usb-storage: device scan complete
Jun  1 11:13:19 enterprise NetworkManager: <debug info>^I[1149174799.079264] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a410_415DEF10030029041104_if0_scsi_host_scsi_device_lun0').
Jun  1 11:13:19 enterprise NetworkManager: <debug info>^I[1149174799.190662] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/storage_serial_LEXAR_JUMPDRIVE_SPORT_415DEF10030029041104').
Jun  1 11:13:19 enterprise NetworkManager: <debug info>^I[1149174799.192290] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/usb_device_5dc_a410_415DEF10030029041104_if0_scsi_host_scsi_device_lun0_scsi_generic').
Jun  1 11:13:19 enterprise NetworkManager: <debug info>^I[1149174799.254062] nm_hal_device_added (): New device added (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_41B1_F4D0').
Jun  1 11:13:19 enterprise kernel: [4295245.840000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
``` 
So I guess it looks like there is something wrong with External Hard Drive or its Partition Table, huh?

EDIT:  Still more information:

I booted Knoppix 4.0 (I think it was 4.0.2 to be precise) just to see if the USB hard drive would work...it did.  I noted two things:  Knoppix uses kernel version 2.6.12.  Module ehci_hcd (USB 2.0 Driver) was not loaded in Knoppix.  Don't know if that helps or not, just adding the to pile of info.

---

### Post by skyshark88 on 2006-06-01
the kernel you are using might not have scsi capabilities.........

---

### Post by skyshark88 on 2006-06-01
scsi2 : SCSI emulation for USB Mass Storage devices

3rd line of code from your last post it is mising from your first post and I prasume you need a kernel upgrade...... how i dont know

---

### Post by skyshark88 on 2006-06-01
Dude do a search on your synaptic package manager and try adding a couple of scsi tools............search [COLOR="Red"]scsi[/COLOR]

---

### Post by ScatterBrain on 2006-06-06
**skyshark88:** That line does appear when I plug in the drive under Dapper.  And I already have all the SCSI stuff loaded - my internal Hard Drive is seen as a SCSI device via "libata".

I've tried everything I can think of - including blacklisting the ehci_hcd module and nothing has worked at this point.  I'm almost 100% convinced that it has something to do with Ubuntu's vanilla kernels.  I'm just not sure that I'm ready to start off down the road to compile my own just yet.

One other interesting thing to note:  A co-worker of mine plugged the drive into his Ubuntu Dapper laptop (an Inspiron 8600) and he gets the same results as I do.  But yet, the drive works in Windows on both his and my laptop.  It's not the hardware, it has to be either something in Ubuntu Dapper or the kernel.

---

### Post by ScatterBrain on 2006-06-08
**[COLOR=Navy]** Bump **[/COLOR]**

Does anyone know what this may be?

Just for the record, I've added Fedora Core 5 and Knoppix 5.0.1 to the list of OSes that the drive works on.  It's defianitly an Ubuntu/Ubuntu Kernel problem as far as I can see.

I've filed a bug on Launchpad - I'm assuming that this is a Kernel issue, but I have no way of knowing what I need to do to fix it.

---

### Post by Aurelias on 2006-06-09
Hey, I've been having a reasonably similar problem with my external.  Instead of immediately failing, it would work for a while, and then start getting those random i/o errors.  What I did is modprobe -r ehci-hcd before plugging it into my laptop so that the ohci drivers would take over the automount.  It's much, *much* slower, but it's solid.  You said you already blacklisted the ehci-hcd module, though, so I'm not sure how useful this is.
-Aurelias

---

### Post by Nginter1 on 2006-07-13
I have the same drive - It would work a day then quit. First if I was hybernating my computer it would not wake the USB port up even though it was set to.(There is many people that have complained about this and have asked for a fix).

Second when it started working was when I went into computer management in the control panel in adminstrator and right clicked on removable drive and had to initialize the drive. It has worked fine since than. 

I don't know why but it has not errored or not worked in about a month. 

Hope it makes sense.

---

### Post by Nginter1 on 2006-07-13
:KS I also forgot to tell you that Western Digital on their web site tell you under technical support you have to initialize the drive failure to do so you will not be able to do anything!!! Just fyi - as I said I was frustrated cause it did not work for about a month and then I finally went to their site and found the information burried. 

Regards:)

---

### Post by Pragmatist on 2006-08-11
I'm having similar problems with a 320GB WD USB drive on Ubuntu.  Basically, my machine would completely lock up during a file-transfer and I'd have to physically shut it down.  Another, less severe, problem was that the drive would only be read-only despite the entry in /etc/fstab and the output of the mount command to the contrary.

A couple of suggestions:

1.) Try some liveCDs.  
I had no problems with this drive before I changed from Breezy to Dapper, and the drive worked on other OSes so I felt the problem is unlikely to be the drive itself.  Sure enough, the drive worked perfectly using the Kubuntu LiveCD and on an old Knoppix LiveCD.  It also worked fine on another machine running Dapper with no upgrades or additions.  I gave a friend my Ubuntu Dapper LiveCD, so I didn't get to try that one yet.

2.) Try using the drive in a virtual terminal (CTRL-ALT-Fn  where n is 1,2,3,4,5, or 6)  

3.) Try other mounting options.
When the drive worked in Kubuntu, I wrote down the entry in it's /etc/fstab
 and then put it in Ubuntu's /etc/fstab.  This completely solved my read-only problem.  Here is the entry:
```
/dev/mybook     /media/mybook   vfat        rw,nosuid,nodev,quiet,shortname=mixed,uid=1000,gid=1000,umask=077,iocharset=utf8     0       1
``` Make the last number a 0 instead of a 1 if you don't want the drive automatically mounted on startup.  FYI setting the charset to  utf8 may cause other problems if your drive is formatted as FAT.  This is something I'm currently looking into.  I just copied the entry that the other Linux systems used.  However, it might be worth experimenting without the utf option.

4.) Try an earlier kernel.
 This seemed to end the freezes!  When your booting up, you'll see an opportunity to press ESC as GRUB is loading.  This will give you a menu with various kernel listings.  Pick an earlier one like 2.6.15.23  instead of 2.6.15.26 (if you upgraded).  This was especially logical in my case, since I knew the hardware worked on other systems (and on the system in question with another version of Ubuntu).  If this works for you, I would think you have three basic options.  One, edit your /boot/grub/menu.lst file and make the older kernel the default (or at least, remove/make longer the time-out and make the kernel menu show by default)  This will make selecting the older kernerl much easier.  Two, wait for newer Kernel upgrades and try them out hoping that the problem is fixed.  Three, make a custom kernel from scratch, or at least recompile a kernel, making sure it has all the options you need.

Final note:  I'm fairly confident that this solved my problem, but if it hasn't I'll be sure to update you all :)  The only glitch I've had was when I exited GNOME, the system froze.  Consequently, I couldn't log in to GNOME.  So, I just upgrade GNOME and, so far, no problems.   I'm not sure that this last problem has anything to do with the drive, however.

Please let us know if any of this works for any of you.  Thanks.

---

### Post by ssn on 2007-11-20
Hi, how do you initialize a drive from the shell?

---

