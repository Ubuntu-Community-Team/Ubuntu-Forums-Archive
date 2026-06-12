---
title: "USB Thumb drive not working"
date: 2008-07-04
forum: Hardware
---

### Post by valuntahr on 2008-07-04
I recently purchased a 16 GB Adata USB hard thumb drive, and it doesn't mount when I attach it to any USB port. All of my other USB devices work perfectly. 

The output from dmesg | grep -i usb regarding this USB device is 

```

[ 9228.896341] usb 4-3: new high speed USB device using ehci_hcd and address 3
[ 9229.029489] usb 4-3: configuration #1 chosen from 1 choice
[ 3689.751612] usbcore: registered new interface driver libusual
[ 3689.832568] Initializing USB Mass Storage driver...
[ 3689.834226] scsi2 : SCSI emulation for USB Mass Storage devices
[ 3689.837564] usbcore: registered new interface driver usb-storage
[ 3689.837573] USB Mass Storage support registered.
[ 3689.838043] usb-storage: device found at 3
[ 3689.838047] usb-storage: waiting for device to settle before scanning
[ 9236.706928] usb-storage: device scan complete
[ 3696.748645] usb 4-3: reset high speed USB device using ehci_hcd and address 3
[ 3707.822038] usb 4-3: device descriptor read/64, error -110
[ 9295.914104] usb 4-3: device descriptor read/64, error -110
[ 9296.129970] usb 4-3: reset high speed USB device using ehci_hcd and address 3
[ 9319.967349] usb 4-3: device descriptor read/64, error -110
[ 9326.197168] usb 4-3: USB disconnect, address 3
[ 3729.271152] usb 4-3: new high speed USB device using ehci_hcd and address 4
[ 9328.887309] usb 4-3: configuration #1 chosen from 1 choice
[ 9328.951606] scsi3 : SCSI emulation for USB Mass Storage devices
[ 9328.957053] usb-storage: device found at 4
[ 9328.957064] usb-storage: waiting for device to settle before scanning
[ 9335.614666] usb-storage: device scan complete
[ 9342.759261] usb 4-3: reset high speed USB device using ehci_hcd and address 4
[ 9350.211053] usb 4-3: USB disconnect, address 4
[ 9352.150336] usb 1-2: USB disconnect, address 3
[ 3746.386761] usb 4-1: new high speed USB device using ehci_hcd and address 5
[ 9371.629169] usb 4-1: configuration #1 chosen from 1 choice
[ 3746.479738] scsi4 : SCSI emulation for USB Mass Storage devices
[ 3746.489408] usb-storage: device found at 5
[ 3746.489414] usb-storage: waiting for device to settle before scanning
[ 9378.652140] usb-storage: device scan complete
[ 9383.067497] usb 4-1: USB disconnect, address 5
[ 9386.457793] usb 4-2: new high speed USB device using ehci_hcd and address 6
[ 9386.590967] usb 4-2: configuration #1 chosen from 1 choice
[ 9386.656064] scsi5 : SCSI emulation for USB Mass Storage devices
[ 9386.662868] usb-storage: device found at 6
[ 9386.662880] usb-storage: waiting for device to settle before scanning
[ 9394.131690] usb-storage: device scan complete
[ 4028.766975] usb 4-2: reset high speed USB device using ehci_hcd and address 6
[ 9427.794941] usb 4-2: device descriptor read/64, error -110
[ 9449.968504] usb 4-2: device descriptor read/64, error -110
[ 9450.184409] usb 4-2: reset high speed USB device using ehci_hcd and address 6
[ 9451.111258] usb 4-2: USB disconnect, address 6
[ 3792.305579] usb 4-2: new high speed USB device using ehci_hcd and address 7
[ 9486.463777] usb 4-2: configuration #1 chosen from 1 choice
[ 9486.476354] scsi6 : SCSI emulation for USB Mass Storage devices
[ 9486.481607] usb-storage: device found at 7
[ 9486.481617] usb-storage: waiting for device to settle before scanning
[ 9493.881825] usb-storage: device scan complete
[10021.163104] usb 4-2: USB disconnect, address 7
[121216.551153] usb 4-2: new high speed USB device using ehci_hcd and address 8
[121216.684455] usb 4-2: configuration #1 chosen from 1 choice
[121216.689064] scsi7 : SCSI emulation for USB Mass Storage devices
[121216.689982] usb-storage: device found at 8
[121216.689990] usb-storage: waiting for device to settle before scanning
[121223.785827] usb-storage: device scan complete
[121231.002207] usb 4-2: reset high speed USB device using ehci_hcd and address 8
[121250.935173] usb 4-2: device descriptor read/64, error -110
[121278.730189] usb 4-2: device descriptor read/64, error -110
[48483.194969] usb 4-2: reset high speed USB device using ehci_hcd and address 8
[90945.236878] usb 4-2: device descriptor read/64, error -110
[48506.492077] usb 4-2: device descriptor read/64, error -110
[48506.710863] usb 4-2: reset high speed USB device using ehci_hcd and address 8
[48514.089960] usb 4-2: device not accepting address 8, error -110
[48514.201860] usb 4-2: reset high speed USB device using ehci_hcd and address 8
[121371.370199] usb 4-2: device not accepting address 8, error -110
[121371.370511] usb 4-2: USB disconnect, address 8
[48520.135316] usb 4-2: new high speed USB device using ehci_hcd and address 9
[48533.630330] usb 4-2: device descriptor read/64, error -110
[121438.071992] usb 4-2: device descriptor read/64, error -110
[121438.287906] usb 4-2: new high speed USB device using ehci_hcd and address 10
[121465.885544] usb 4-2: device descriptor read/64, error -110
[91080.511062] usb 4-2: device descriptor read/64, error -110
[121488.398831] usb 4-2: new high speed USB device using ehci_hcd and address 11
[91092.598164] usb 4-2: device not accepting address 11, error -110
[121504.397536] usb 4-2: new high speed USB device using ehci_hcd and address 12
[72871.444463] usb 4-2: device not accepting address 12, error -110
[122266.992936] usb 4-2: new high speed USB device using ehci_hcd and address 13
[122267.126112] usb 4-2: configuration #1 chosen from 1 choice
[122267.134325] scsi8 : SCSI emulation for USB Mass Storage devices
[122267.140920] usb-storage: device found at 13
[122267.140932] usb-storage: waiting for device to settle before scanning
[122274.354156] usb-storage: device scan complete
[122281.561424] usb 4-2: reset high speed USB device using ehci_hcd and address 13
[122305.579238] usb 4-2: device descriptor read/64, error -110
[122325.449061] usb 4-2: device descriptor read/64, error -110
[48901.598765] usb 4-2: reset high speed USB device using ehci_hcd and address 13
[48909.480171] usb 4-2: device descriptor read/64, error -110
[122367.378066] usb 4-2: device descriptor read/64, error -110
[122367.593961] usb 4-2: reset high speed USB device using ehci_hcd and address 13
[122381.397606] usb 4-2: device not accepting address 13, error -110
[48923.937920] usb 4-2: reset high speed USB device using ehci_hcd and address 13
[122395.445960] usb 4-2: device not accepting address 13, error -110
[122395.446273] usb 4-2: USB disconnect, address 13
[122395.668083] usb 4-2: new high speed USB device using ehci_hcd and address 14
[122416.990232] usb 4-2: device descriptor read/64, error -110
[122437.943550] usb 4-2: device descriptor read/64, error -110
[48946.602953] usb 4-2: new high speed USB device using ehci_hcd and address 15
[122463.229814] usb 4-2: device descriptor read/64, error -110
[122484.314892] usb 4-2: device descriptor read/64, error -110
[122484.530797] usb 4-2: new high speed USB device using ehci_hcd and address 16
[48970.806655] usb 4-2: device not accepting address 16, error -110
[91838.413071] usb 4-2: new high speed USB device using ehci_hcd and address 17
[122514.621827] usb 4-2: device not accepting address 17, error -110
[49029.324937] usb usb4: USB disconnect, address 1
[49029.329025] ehci_hcd 0000:00:1d.7: USB bus 4 deregistered
[122645.650338] usb 1-2: new full speed USB device using uhci_hcd and address 4
[49037.535920] usb 1-2: device descriptor read/64, error -110
[91979.991373] usb 1-2: device descriptor read/64, error -110
[122688.165438] usb 1-2: new full speed USB device using uhci_hcd and address 5
[122710.115770] usb 1-2: device descriptor read/64, error -110
[122734.785848] usb 1-2: device descriptor read/64, error -110
[122735.001755] usb 1-2: new full speed USB device using uhci_hcd and address 6
[49073.188717] usb 1-2: device not accepting address 6, error -110
[122755.134556] usb 1-2: new full speed USB device using uhci_hcd and address 7
[122770.929702] usb 1-2: device not accepting address 7, error -110
[122864.527145] usb 1-2: new full speed USB device using uhci_hcd and address 8
[122885.480760] usb 1-2: device descriptor read/64, error -110
[122905.085927] usb 1-2: device descriptor read/64, error -110
[122905.301821] usb 1-2: new full speed USB device using uhci_hcd and address 9
[122928.156624] usb 1-2: device descriptor read/64, error -110
[122950.616487] usb 1-2: device descriptor read/64, error -110
[122950.957082] usb 1-2: new full speed USB device using uhci_hcd and address 10
[122964.730185] usb 1-2: device not accepting address 10, error -110
[122964.842177] usb 1-2: new full speed USB device using uhci_hcd and address 11
[122978.354259] usb 1-2: device not accepting address 11, error -110
[124392.955397] usb 1-2: new low speed USB device using uhci_hcd and address 12
[124393.132550] usb 1-2: configuration #1 chosen from 1 choice

```

This device was working perfectly a few days ago, and works properly on another machine that's running windows XP. I'm currently running Ubuntu Hardy. Any help would be much appreciated.

---

### Post by evanphelps on 2008-08-07
Any responses to this error yet.

I, too, have a PD16 USB drive that only seems to work on MS Windows.  My dmesg output is the same as valutahr's.  I've taken numerous measures attempting to get it to work, including playing with ehci-hcd, uhci-hcd, acpi options, etc.  The device never even gets a /dev/* entry.

uname
=====
Linux 2.6.24-20-generic #1 SMP Mon Jul 28 13:49:52 UTC 2008 i686 GNU/Linux

dmesg output
============

[ 3250.446047] usb 1-3: new high speed USB device using ehci_hcd and address 7
[ 3250.579032] usb 1-3: configuration #1 chosen from 1 choice
[ 3250.580107] scsi3 : SCSI emulation for USB Mass Storage devices
[ 3250.580506] usb-storage: device found at 7
[ 3250.580512] usb-storage: waiting for device to settle before scanning
[ 3255.573316] usb-storage: device scan complete
[ 3261.179679] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[ 3276.277105] usb 1-3: device descriptor read/64, error -110
[ 3291.482429] usb 1-3: device descriptor read/64, error -110
[ 3291.694319] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[ 3306.791666] usb 1-3: device descriptor read/64, error -110
[ 3321.993005] usb 1-3: device descriptor read/64, error -110
[ 3322.212785] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[ 3332.606743] usb 1-3: device not accepting address 7, error -110
[ 3332.718746] usb 1-3: reset high speed USB device using ehci_hcd and address 7
[ 3343.116624] usb 1-3: device not accepting address 7, error -110
[ 3343.116700] scsi 3:0:0:0: Device offlined - not ready after error recovery
[ 3343.117149] usb 1-3: USB disconnect, address 7
[ 3343.228521] usb 1-3: new high speed USB device using ehci_hcd and address 8

The pattern repeats with multiple addresses.

---

### Post by FXEF on 2008-08-07
It could be that these A-Data drives are not compatiable with Linux. I saw elsewhere that it would not work with Fedora9 either. You may need to contact A-Data.

---

### Post by dsmorgan6922 on 2008-08-08
I'd like to bump this as I'm having a similar problem. I just got a Cosair usb stick and was able to mount it cleanly the first time and backup some data and then I have been unable to mount it since. I have tried to mount it on vista and it works just fine :\

Here is some output:

uname -a
```

Linux <LAPTOP NAME>  2.6.24-19-generic #1 SMP Fri Jul 11 23:41:49 UTC 2008 i686 GNU/Linux

```

dmesg:
```

[ 2593.370415] usb 7-2: new high speed USB device using ehci_hcd and address 2
[ 2593.504166] usb 7-2: configuration #1 chosen from 1 choice
[ 2593.615088] usbcore: registered new interface driver libusual
[ 2593.630449] Initializing USB Mass Storage driver...
[ 2593.631325] scsi2 : SCSI emulation for USB Mass Storage devices
[ 2593.632159] usbcore: registered new interface driver usb-storage
[ 2593.632163] USB Mass Storage support registered.
[ 2593.632491] usb-storage: device found at 2
[ 2593.632493] usb-storage: waiting for device to settle before scanning
[ 2598.627269] usb-storage: device scan complete
[ 2604.235638] usb 7-2: reset high speed USB device using ehci_hcd and address 2
[ 2619.338252] usb 7-2: device descriptor read/64, error -110
[ 2634.545001] usb 7-2: device descriptor read/64, error -110
[ 2634.760859] usb 7-2: reset high speed USB device using ehci_hcd and address 2
[ 2649.864829] usb 7-2: device descriptor read/64, error -110
[ 2665.071569] usb 7-2: device descriptor read/64, error -110
[ 2665.286267] usb 7-2: reset high speed USB device using ehci_hcd and address 2
[ 2675.687919] usb 7-2: device not accepting address 2, error -110
[ 2675.799907] usb 7-2: reset high speed USB device using ehci_hcd and address 2
[ 2686.201709] usb 7-2: device not accepting address 2, error -110
[ 2686.201775] usb 7-2: USB disconnect, address 2
[ 2686.201994] scsi 2:0:0:0: Device offlined - not ready after error recovery
[ 2686.314462] usb 7-2: new high speed USB device using ehci_hcd and address 3
[ 2701.416254] usb 7-2: device descriptor read/64, error -110
[ 2716.622992] usb 7-2: device descriptor read/64, error -110
[ 2716.838864] usb 7-2: new high speed USB device using ehci_hcd and address 4
[ 2731.941668] usb 7-2: device descriptor read/64, error -110
[ 2747.148574] usb 7-2: device descriptor read/64, error -110
[ 2747.364248] usb 7-2: new high speed USB device using ehci_hcd and address 5
[ 2757.766917] usb 7-2: device not accepting address 5, error -110
[ 2757.877846] usb 7-2: new high speed USB device using ehci_hcd and address 6
[ 2768.279830] usb 7-2: device not accepting address 6, error -110

```

---

### Post by silkstone on 2008-08-08
The problem may be that some USB sticks have a hidden partition for password encryption, and that is not recognised by Linux so the drive won't mount.

If you look at the drive in gparted, can you see anything?

I've not had this problem so far, but I've seen two possible solutions. One is to use Windows to remove the password protection, and the other is to reformat the drive in gparted or Windows.

---

### Post by dsmorgan6922 on 2008-08-08
It's not showing up in gparted. I did mount the drive in windows and it was using a FAT32 file system and I don't remember seeing a password field or anything... :(

---

### Post by silkstone on 2008-08-08
Mmmm.. the only other suggestion would be to reformat it in Windows, but it does sound as if there may be a more fundamental compatibility issue.

---

### Post by papsynot on 2008-08-08
I have a similar problem, but I know it's because the stick is faulty - I can't even format it in windows. But is it possible to see the raw contents of the USB stick without formatting it?

---

### Post by mc4man on 2008-08-08
i have no experience with these flash drives but possibly the issue is related to them being 'readyboost' enhanced.
the website does say > * Linux: Kernel 2.4 or later
so maybe you should call tech support
From windows concerning 'readyboost'

> An external ReadyBoost-capable device might be removed at any time, but ReadyBoost technology ensures there is no interruption of system service or loss of data. All data writes are made to the hard disk before being copied to the flash device, so every bit of data held within the flash device is safely duplicated on the hard disk. ReadyBoost also encrypts the content for use only on the PC system where the data was generated.

additionally from manu.
> Additionally, data on the removable memory device is encrypted to help prevent inappropriate access to data when the device is removed. 


maybe you need to set up encryption/decryption on removable drives from the linux side

---

### Post by silkstone on 2008-08-08
I have a couple of 8GB flash drives that are ReadyBoost enabled, and they work OK with Ubuntu. The puzzle is that dsmorgan's drive isn't being picked up by gparted. I do wonder if Windows Disk Manager will show a hidden partition.

---

### Post by dsmorgan6922 on 2008-08-08
So what should I do? I do have data on the drive that I'd like to get into ubuntu (but I could get around this by copying it to my iPod and then to ubuntu). Should I just do the double copy and then re-do the partition on the drive?

---

### Post by silkstone on 2008-08-08
The most important thing is the data. Make sure you have that on your Windows PC or wherever, and then you can copy it to your Ubuntu machine with another USB stick or anything else that works.

Then, if you'd like to try getting the Corsair drive working with Ubuntu, I would look at it in Windows Disk Manager. (I can't remember exactly how you get to that, but I think it's under Computer Management in Control Panel.)

See what shows up there, and then, if you like, reformat the drive FAT32.

If it still doesn't work in Ubuntu, there is something deeper at fault here, but I don't know what.

Another thing to look at is the drive properties (right click on it in My Computer) and see if anything shows up. Did it come with any software for password encryption? That may be on the drive itself.

Why is life never simple? :)

---

### Post by dsmorgan6922 on 2008-08-08
I'm going to start the copy procedure and reformat the drive in FAT32.

I looked at the usb drive in as many Windows menus as I could find (in Vista Business) and didn't see anything unusual. We'll see what happens after the reformat.

I'm still really confused as to why the drive would mount on the first try and fail everytime after that... This sounds more like a fundamental linux issue then just a drive issue but we'll see.

The copy procedure will probably take over night here at this point so I'll report back tomorrow.

---

### Post by evanphelps on 2008-08-09
I made no more progress with the issue, but I did hear back from A-Data, and they have opened a ticket for me.  They have the specific product number, and they're now trying to reproduce the error.

Thanks for everyone's suggestions thus far.  To give you an idea of what I've already done:

1. removed encrypted partition
2. reformatted to FAT32 and FAT
3. tweaked acpi, irq, ehci, uhci, ohci
4. tried on multiple distributions of linux with various recent kernels

The partition changes were done via Windows, because gparted, fdisk, etc. will not pick up the drive while in Linux.

I probably did more, but these were the main things that I tried.

I'll post more after I get an update from A-Data.

---

### Post by dsmorgan6922 on 2008-08-09
I reformated the drive to no avail (in Windows Vista Business to FAT32). Sigh....

Any suggestions?

---

### Post by evanphelps on 2008-08-16
Update: A-Data replied with an offer to replace my usb drive, but I'm very skeptical that a different one will work.

---

### Post by oracel on 2008-08-18
Hi! Same thing happening here using a Fujifilm Finepix S6500 camera when connecting it as usual to USB. Used to work very well just a week or two ago. I recently installed Virtualbox, could that have borked something?

---

### Post by evanphelps on 2008-08-18
I am success!  And you can too...

Please review the previous posts to check the specific problem that this corrects. My syslog errors were about the same as the original poster.

I downloaded hddguru.com's low-level format tool and reformatted the usb drive. Note that this is NOT a high-level formatter like most partition managers that allow you to format in FAT, NTFS, etc.  After performing the low-level format, I was able to perform a high-level format via gparted, and the drive mounts just fine.

I am sending the "fix" to the A-Data representative who offered to send me an RMA.

---

### Post by evanphelps on 2008-08-18
> **evanphelps said:**
> I am success!  And you can too...

Please review the previous posts to check the specific problem that this corrects. My syslog errors were about the same as the original poster.

I downloaded hddguru.com's low-level format tool and reformatted the usb drive. Note that this is NOT a high-level formatter like most partition managers that allow you to format in FAT, NTFS, etc.  After performing the low-level format, I was able to perform a high-level format via gparted, and the drive mounts just fine.

I am sending the "fix" to the A-Data representative who offered to send me an RMA.

Short-lived success.  I was able to use the drive until I unplugged it the first time.  It was progress, but it was to no avail.  I am failure.. and you can too.

---

### Post by valuntahr on 2008-08-21
hmm, I had misplaced the USB key for a while so I was unable to continue testing the USB device. I tried to solve the problem earlier today but dmesg kept displaying these 2 error messages no matter which solution I tried, device not accepting address 10, error -110 and device descriptor read/64, error -110. 

I recently had occasion to try to use the device on a windows XP machine again and I came across something interesting that may be related to the problem at hand. A non readyboost enabled USB drive mounts as a regular external storage drive, while the Adata USB key mounts as a virtual DVD-RAM drive. Would it be possible that the same property that causes the adata drive to mount differently in windows be the issue that's preventing ubuntu from recognizing and mounting the drive properly?

---

### Post by evanphelps on 2008-08-21
> **valuntahr said:**
> hmm, I had misplaced the USB key for a while so I was unable to continue testing the USB device. I tried to solve the problem earlier today but dmesg kept displaying these 2 error messages no matter which solution I tried, device not accepting address 10, error -110 and device descriptor read/64, error -110. 

I recently had occasion to try to use the device on a windows XP machine again and I came across something interesting that may be related to the problem at hand. A non readyboost enabled USB drive mounts as a regular external storage drive, while the Adata USB key mounts as a virtual DVD-RAM drive. Would it be possible that the same property that causes the adata drive to mount differently in windows be the issue that's preventing ubuntu from recognizing and mounting the drive properly?

That is odd; although I do have another Readyboost capable usb drive (only 8GB) that works fine on Linux.  I finally gave up on the A-Data drive. It's too much of a time drain.

---

### Post by valuntahr on 2008-08-21
same with my 2 GB one, that one works perfectly. I wonder why the Adata varient so so hard to get working under linux. I may end up purchasing another drive if I can't get this one working. Are there any suggestions as far as 16GB (preferably) drives that work well under linux?

---

### Post by marioitalo on 2008-10-01
I found a solution to that problem (apparently this is about the time needed to the device wake-up):
At /etc/modprobe.d/options I added the line:
options scsi_mod inq_timeout=20
Then I tried to unload and load the module(scsi_mod), but didn't work, because this option was in initrd file. So I reinstalled the package linux-image-* what forced the system to make a new initrd file and use the new configuration (of course there is a better way to do that but I didn't want to search how to), then, after a reboot, voilá, the pen drive was back to life.\\:D/
I hope this help someone.

---

