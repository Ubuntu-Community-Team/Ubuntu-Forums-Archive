---
title: "Missing IDE drives?"
date: 2008-08-04
forum: General Help
---

### Post by Metallinut on 2008-08-04
Anyone know what may be happening here? Or what I can do to troubleshoot further?

I have my OS, /home & swap partitions on an internal SATA drive (/dev/sda)

I HAD an IDE drive for ~/olddrive which was /dev/sdb
I had another IDE drive mounted at ~/media2 which was /dev/sdc

I then had my m/b go.  I replaced an AMD m/b cpu combo with an Intel based m/b & cpu.  Booted up, and everything seemed fine.  I saw all drives, etc.

I got a drobo, hooked it up via usb, and mounted it at /dev/sdd.  No problems, and I moved 90% of my data from the 2 IDE drives over to it.  

I shut the whole system down for a 1 week vacation.  When I got back, I booted up, and fschk failed...

Further diagnosing found that the /dev/sdb drive was being seen, but not mounted (by UUID, but that shouldn't have changed), but /dev/sdc is nowhere to be found.  It appears that Ubuntu no longer sees the actual drive itself.

So now I have /, /home & swap on /dev/sda, and the Drobo on /dev/sdb.

I don't care about ~/olddrive, as I've gotten all the data off.  But the drive I no longer see (~/media2) is one that still has data on it!  

How can I troubleshoot this to find out if the OS actually sees the drive or not?

Thanks,

---

### Post by Taxman415a on 2008-08-04
```
sudo fdisk -l
``` should show what is seen. Also you can have a look at the output of dmesg, perhaps by ```
dmesg |less
``` then you can search for the patterns you see in the fdisk output. They should of course match. Based on your fdsik output we can see what else is going on.

---

### Post by Metallinut on 2008-08-04
```
jp@ubuntu2:~$ sudo fdisk -l
[sudo] password for jp:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00023e08

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2490    20000893+  83  Linux
/dev/sda2            2491       19208   134287335   83  Linux
/dev/sda3           19209       19457     2000092+  82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 2199.0 GB, 2199023185920 bytes
255 heads, 63 sectors/track, 267349 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9abf10c5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      267350  2147483579+  ee  EFI GPT
jp@ubuntu2:~$

```

This is what I'm afraid of!  It acts like it doesn't see the drives at all.

I'm not too familiar with dmesg, so I tried grepping for failed and error, and got these:

```
jp@ubuntu2:~$ dmesg | grep -i -A 5 -B 5 error
[   20.434497] Compat vDSO mapped to ffffe000.
[   20.434573] Checking 'hlt' instruction... OK.
[   20.449620] SMP alternatives: switching to UP code
[   20.450912] Early unpacking initramfs... done
[   20.691365] ACPI: Core revision 20070126
[   20.691461] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   20.693614] CPU0: Intel(R) Core(TM)2 Duo CPU     E7200  @ 2.53GHz stepping 06
[   20.693801] SMP alternatives: switching to SMP code
[   20.694413] Booting processor 1/1 eip 3000
[   20.704743] Initializing CPU#1
[   20.785086] Calibrating delay using timer specific routine.. 5066.91 BogoMIPS (lpj=10133829)
--
[   20.954643] Setting up standard PCI resources
[   20.959618] ACPI: EC: Look up EC in DSDT
[   20.963014] ACPI: Interpreter enabled
[   20.963082] ACPI: (supports S0 S1 S3 S4 S5)
[   20.963427] ACPI: Using IOAPIC for interrupt routing
[   20.963615] Error attaching device data
[   20.963706] Error attaching device data
[   20.963797] Error attaching device data
[   20.963888] Error attaching device data
[   20.968974] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   20.970471] PCI: Transparent bridge - 0000:00:0a.0
[   20.970753] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[   20.970897] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.P0P1._PRT]
[   20.970990] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.BR10._PRT]
jp@ubuntu2:~$

```

And:
```
jp@ubuntu2:~$ dmesg | grep -i -A 5 -B 5 failed
[   26.532073]  sda: sda1 sda2 sda3
[   26.556945] sd 2:0:0:0: [sda] Attached SCSI disk
[   26.760401] Attempting manual resume
[   26.760468] swsusp: Resume From Partition 8:3
[   26.760469] PM: Checking swsusp image.
[   26.760532] PM: Resume from disk failed.
[   26.794094] kjournald starting.  Commit interval 5 seconds
[   26.794102] EXT3-fs: mounted filesystem with ordered data mode.
[   34.612972] /build/buildd/linux-2.6.24/drivers/hid/usbhid/hid-core.c: timeout initializing reports
[   34.613116] input: Logitech Inc. WingMan RumblePad as /devices/pci0000:00/0000:00:04.0/usb2/2-2/2-2:1.0/input/input3
[   34.613211] input,hidraw1: USB HID v1.10 Joystick [Logitech Inc. WingMan RumblePad] on usb-0000:00:04.0-2
jp@ubuntu2:~$

```

Not sure what I'm looking at...

---

### Post by Taxman415a on 2008-08-04
Yeah that's not enough of the dmesg to tell. It may help to post it to a pastebin and post the link, but I'm thinking now it won't tell anything. Have you tried the simple things like checking if all 3 drives show up in the BIOS? Then try booting from an Ubuntu livecd and see what drives show up there. Also can you give a simple summary of what drives you have attached now and what type of drive (ATA, SATA, USB) is the one that is not showing up? Your first post is very hard to follow.

---

### Post by Metallinut on 2008-08-05
Yeah, sorry about the confusion.  I'll have to wait until I get home tonight to try your recommendations...but I'll post the results here.  

Another route I may just try, is to pop the drive into an external USB enclosure, and see if I can just read the data off...

---

### Post by Metallinut on 2008-08-05
Well...totally bizarre, but after a reboot, the drives are magically delicious...I mean back (sorry, eating ice cream)


So alls well that ends well I guess...but weird.

Thanks!

---

### Post by Taxman415a on 2008-08-05
Oh good stuff. You may want to check the physical connections, power supply, etc. Glad they're working. You may also want to install the smartmontools package and run ```
sudo smartctl -a /dev/sda
``` and the same for sdb, c, etc to see if there are any detectable problems with the drives. I don't know much about the output, but you can google for it. Your issues may be signs the drives are failing, so you should make good backups.

---

### Post by alguin2 on 2008-08-07
Your problem looks very similar to my problem.  My ubuntu HH (kernel  2.6.24-17-generic) has been functioning swimmingly well since installation a few months ago.   

Suddenly, last week, the machine (samuel): 
1) Decided that it won't anymore boot into the gnome session. 
   Now I get a tty-style text login (a-la UNIX UTS login). I login,
   do a "xinit", start 2 xterms (raw X sessions without window mgr).
   Only after I run gnome-session in one of the XTerms do I get my
   familiar gnome desktop.
 
2) It stopped recognizing my external 250Gbyte Maxtor USB2 external drive.  I have no work-around/solution in Linux.  I can only access the external USB drive by re-booting to Vista.  

What's weird is that the dmesg errors are very similar to the errors in this thread.  

I ran the all detailed system tests supplied by HP (I have a HP a6400f) in a diagnostics partition, and all went well. I also scanned all internal and external disks using BitDefender Virus scanner... and all checked out OK.  

NOTHING changed in my Ubuntu system.  I'm careful not to change anything in the system because I know from past experience that once you get a Linux system up and running, you don't want to make too many changes that can screw you up.

However, I do remember that Microsoft had several "UPDATES" that needed installing, which I did install the day before my Ubuntu machine stopped re-booting correctly. 


So... here are the circumstances.... 
1) No changes made in the system hardware, which has been functioning great for the past few months (ie. since Ubuntu install); 
2) All hardware checks out OK as per the manufacturer's high and low-level diagnostics;
3) Vista able to see the external drive and access it fully
4) Last real change to any part of the system was a package of automated "UPDATES" by Microsoft for Vista....

... I'm wondering if Microsoft installed some "feature" that ensures failure to mount my USB drive?? This reminds me of one problem that I encountered when initially installing Ubuntu:  When shutting down, Microsoft Vista apparently logically "shuts down" the 1Gig RealTek network card, and unless it's properly woken up on powerup, the card and thus the network is inaccessible.  Microsoft sees this as a feature, and not as a denial of service on their part.  Thankfully, the manufacturer created an updated driver that allows Linux to wake up the device. 
  
Anyways, below is the similar error that I get in dmesg.... 

> 
$ dmesg | grep -i -A 5 -B 5 error
[   30.256831] Compat vDSO mapped to ffffe000.
[   30.256842] Checking 'hlt' instruction... OK.
[   30.273014] SMP alternatives: switching to UP code
[   30.274365] Early unpacking initramfs... done
[   30.535842] ACPI: Core revision 20070126
[   30.535875] ACPI: Looking for DSDT in initramfs... error, file /DSDT.aml not found.
[   30.560102] CPU0: Intel(R) Pentium(R) Dual  CPU  E2200  @ 2.20GHz stepping 0d
[   30.560115] SMP alternatives: switching to SMP code
[   30.560725] Booting processor 1/1 eip 3000
[   30.570774] Initializing CPU#1
[   30.688200] Calibrating delay using timer specific routine.. 4399.43 BogoMIPS (lpj=8798873)
--
[   30.857081] Setting up standard PCI resources
[   30.860132] ACPI: EC: Look up EC in DSDT
[   30.863001] ACPI: Interpreter enabled
[   30.863004] ACPI: (supports S0 S1 S3 S4 S5)
[   30.863016] ACPI: Using IOAPIC for interrupt routing
[   30.863167] Error attaching device data
[   30.863200] Error attaching device data
[   30.863230] Error attaching device data
[   30.863260] Error attaching device data
[   30.868313] ACPI: PCI Root Bridge [PCI0] (0000:00)
[   30.869164] PCI quirk: region 0800-087f claimed by ICH6 ACPI/GPIO/TCO
[   30.869167] PCI quirk: region 0480-04bf claimed by ICH6 GPIO
[   30.869919] PCI: Transparent bridge - 0000:00:1e.0
[   30.869951] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]



Any ideas on how I can get back my external USB drive?

Thanks in advance.

---

### Post by Taxman415a on 2008-08-07
alguin, it's hard to say, but it would definitely take a lot of hard evidence to verify any sneaky business like that. In any case, what system messages do you get when you unplug the USB drive and plug it back in? dmesg|tail should work. If you get something there and not on reboot then it may very well be related to the ACPI error you see. I don't know much about ACPI details. I do know there are some bugs in Linux handling of ACPI and it seems some of those are MS induced bugs/features.

---

### Post by Metallinut on 2008-08-07
I found this little ditty in my travels, to get USB devices 'reset'.  It may be worth a try for you...
```

sudo modprobe -vr ehci_hcd
sudo modprobe -v ehci_hcd

```

---

