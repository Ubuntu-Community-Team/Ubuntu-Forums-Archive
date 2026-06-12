---
title: "External USB Hard Drive fails to mount!?"
date: 2005-07-11
forum: Hardware &amp; Laptops
---

### Post by Chongo on 2005-07-11
Dear All,

I'm trying to make the switch from Windows XP to Ubuntu 5.04 at the moment, but have been prevented from doing so by the latter's failure to mount my external hard drive.

The drive in question is a Lacie d2 200GB USB / Firewire number, and works fine on Windows. I formatted it in FAT32 with Partition Magic. When you plug it in, the USB Mass Storage driver is correctly identified and loaded, but then nothing happens, and it seems to have some kind of buffer error?

The drive continues to work fine in Windows though, so I'm not sure what's wrong or what I can do. If I can't get it to work, then I can't use Linux, because all of my stuff is on this drive! :-(

ieee80211_crypt: registered algorithm 'NULL'
ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 0.19
ipw2200: Copyright(c) 2003-2004 Intel Corporation
ACPI: PCI interrupt 0000:04:02.0[A] -> GSI 21 (level, low) -> IRQ 21
ipw2200: Detected Intel PRO/Wireless 2915ABG Network Connection
NET: Registered protocol family 17
tg3: eth0: Link is up at 1000 Mbps, full duplex.
tg3: eth0: Flow control is on for TX and on for RX.
usb 5-3.2: khubd timed out on ep0in
usb 5-3.2: device descriptor read/64, error -110
usb 5-3.2: new high speed USB device using ehci_hcd and address 6
usb 5-3.2: khubd timed out on ep0in
usb 5-3.2: device descriptor read/64, error -110
usb 5-3.2: khubd timed out on ep0in
usb 5-3.2: device descriptor read/64, error -110
usb 5-3.4: new low speed USB device using ehci_hcd and address 7
usb 3-2: new full speed USB device using uhci_hcd and address 2
usbcore: registered new driver hiddev
input: USB HID v1.11 Mouse [Microsoft Microsoft IntelliMouse\uffff Explorer] on usb-0 000:00:1d.7-3.4
usbcore: registered new driver usbhid
drivers/usb/input/hid-core.c: v2.0:USB HID core driver
NET: Registered protocol family 10
Disabled Privacy Extensions on device c02f0500(lo)
IPv6 over IPv4 tunneling driver
ACPI: AC Adapter [AC] (on-line)
ACPI: Battery Slot [BAT0] (battery present)
ACPI: Power Button (FF) [PWRF]
ACPI: Lid Switch [LID]
ACPI: Sleep Button (CM) [SLPB]
ibm_acpi: IBM ThinkPad ACPI Extras v0.8
ibm_acpi: [http://ibm-acpi.sf.net/](http://ibm-acpi.sf.net/)
ibm_acpi: dock device not present
drivers/usb/input/hid-input.c: event field not found
ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
IBM machine detected. Enabling interrupts during APM calls.
apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
apm: overridden by ACPI.
cs: IO port probe 0x0100-0x04ff: excluding 0x370-0x377 0x3f0-0x3ff 0x4d0-0x4d7
cs: IO port probe 0x0800-0x08ff: clean.
cs: IO port probe 0x0c00-0x0cff: excluding 0xcf8-0xcff
cs: IO port probe 0x0a00-0x0aff: clean.
eth0: no IPv6 routers present
usb 5-3.2: new full speed USB device using ehci_hcd and address 8
usb 5-3.2: device descriptor read/64, error -32
usb 5-3.2: device descriptor read/64, error -32
usb 5-3.2: new full speed USB device using ehci_hcd and address 9
usb 5-3.2: device descriptor read/64, error -32
usb 5-3.2: device descriptor read/64, error -32
usb 5-3.2: new high speed USB device using ehci_hcd and address 10
Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Initializing USB Mass Storage driver...
scsi2 : SCSI emulation for USB Mass Storage devices
usbcore: registered new driver usb-storage
USB Mass Storage support registered.
usb-storage: device found at 10
usb-storage: waiting for device to settle before scanning
  Vendor: WDC WD20  Model: 00LB-00EDA0       Rev: 15.0
  Type:   Direct-Access                      ANSI SCSI revision: 04
SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
sdb: assuming drive cache: write through
SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
sdb: assuming drive cache: write through
 /dev/scsi/host2/bus0/target0/lun0: p1
Attached scsi disk sdb at scsi2, channel 0, id 0, lun 0
Attached scsi generic sg2 at scsi2, channel 0, id 0, lun 0,  type 0
usb 5-3.2: reset high speed USB device using ehci_hcd and address 10
usb 5-3.2: scsi_eh_2 timed out on ep0in
usb 5-3.2: device descriptor read/64, error -110
usb 5-3.2: scsi_eh_2 timed out on ep0in
usb 5-3.2: device descriptor read/64, error -110
usb 5-3.2: reset high speed USB device using ehci_hcd and address 10
usb 5-3.2: scsi_eh_2 timed out on ep0in
usb 5-3.2: device descriptor read/64, error -110
usb 5-3.2: scsi_eh_2 timed out on ep0in
usb 5-3.2: device descriptor read/64, error -110
scsi: Device offlined - not ready after error recovery: host 2 channel 0 id 0 lu n 0
scsi2 (0:0): rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 0
Buffer I/O error on device sdb, logical block 1
Buffer I/O error on device sdb, logical block 2
Buffer I/O error on device sdb, logical block 3
Buffer I/O error on device sdb, logical block 4
Buffer I/O error on device sdb, logical block 5
Buffer I/O error on device sdb, logical block 6
Buffer I/O error on device sdb, logical block 7
scsi2 (0:0): rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 0
scsi2 (0:0): rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 64
scsi2 (0:0): rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 64
usb 5-3.2: USB disconnect, address 10
scsi: Device offlined - not ready after error recovery: host 2 channel 0 id 1 lu n 0
usb-storage: device scan complete
usb 5-3.2: new high speed USB device using ehci_hcd and address 11
usb 5-3.2: khubd timed out on ep0in
usb 5-3.2: device descriptor read/64, error -110
usb 5-3.2: khubd timed out on ep0in
usb 5-3.2: device descriptor read/64, error -110
usb 5-3.2: new high speed USB device using ehci_hcd and address 12
usb 5-3.2: khubd timed out on ep0in
usb 5-3.2: device descriptor read/64, error -110
usb 5-3.2: khubd timed out on ep0in
usb 5-3.2: device descriptor read/64, error -110
usb 2-2: new full speed USB device using uhci_hcd and address 3
usb 5-4: new high speed USB device using ehci_hcd and address 14
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 14
usb-storage: waiting for device to settle before scanning
  Vendor: WDC WD20  Model: 00LB-00EDA0       Rev: 15.0
  Type:   Direct-Access                      ANSI SCSI revision: 04
SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
sdb: assuming drive cache: write through
SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
sdb: assuming drive cache: write through
 /dev/scsi/host3/bus0/target0/lun0: p1
Attached scsi disk sdb at scsi3, channel 0, id 0, lun 0
Attached scsi generic sg2 at scsi3, channel 0, id 0, lun 0,  type 0
usb 5-4: reset high speed USB device using ehci_hcd and address 14
usb 5-4: scsi_eh_3 timed out on ep0in
usb 5-4: device descriptor read/64, error -110
usb 5-4: scsi_eh_3 timed out on ep0in
usb 5-4: device descriptor read/64, error -110
usb 5-4: reset high speed USB device using ehci_hcd and address 14
usb 5-4: scsi_eh_3 timed out on ep0in
usb 5-4: device descriptor read/64, error -110
usb 5-4: scsi_eh_3 timed out on ep0in
usb 5-4: device descriptor read/64, error -110
scsi: Device offlined - not ready after error recovery: host 3 channel 0 id 0 lu n 0
scsi3 (0:0): rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 0
Buffer I/O error on device sdb, logical block 1
Buffer I/O error on device sdb, logical block 2
Buffer I/O error on device sdb, logical block 3
Buffer I/O error on device sdb, logical block 4
Buffer I/O error on device sdb, logical block 5
Buffer I/O error on device sdb, logical block 6
Buffer I/O error on device sdb, logical block 7
usb 5-4: USB disconnect, address 14
scsi3 (0:0): rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 0
scsi3 (0:0): rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 64
scsi3 (0:0): rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 64
scsi3 (0:0): rejecting I/O to offline device
Buffer I/O error on device sdb, logical block 0

Any help would be massively appreciated!

Bestest,

Chongo

---

### Post by Chongo on 2005-07-11
Also:

Jul 11 12:40:29 localhost kernel: usb 5-3.2: new full speed USB device using ehc i_hcd and address 8
Jul 11 12:40:29 localhost kernel: usb 5-3.2: new full speed USB device using ehc i_hcd and address 9
Jul 11 12:40:37 localhost kernel: usb 5-3.2: new high speed USB device using ehci_hcd and address 10
Jul 11 12:40:38 localhost kernel: Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
Jul 11 12:40:38 localhost kernel: ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
Jul 11 12:40:38 localhost kernel: Initializing USB Mass Storage driver...
Jul 11 12:40:38 localhost usb.agent[8978]:      usb-storage: loaded successfully
Jul 11 12:40:38 localhost kernel: scsi2 : SCSI emulation for USB Mass Storage devices
Jul 11 12:40:38 localhost kernel: usbcore: registered new driver usb-storage
Jul 11 12:40:38 localhost kernel: USB Mass Storage support registered.
Jul 11 12:40:43 localhost kernel:   Vendor: WDC WD20  Model: 00LB-00EDA0       Rev: 15.0
Jul 11 12:40:43 localhost kernel:   Type:   Direct-Access                      ANSI SCSI revision: 04
Jul 11 12:40:43 localhost kernel: SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
Jul 11 12:40:43 localhost kernel: SCSI device sdb: 390721968 512-byte hdwr sectors (200050 MB)
Jul 11 12:40:43 localhost kernel:  /dev/scsi/host2/bus0/target0/lun0: p1
Jul 11 12:40:43 localhost kernel: Attached scsi disk sdb at scsi2, channel 0, id 0, lun 0
Jul 11 12:40:43 localhost kernel: Attached scsi generic sg2 at scsi2, channel 0, id 0, lun 0,  type 0
Jul 11 12:40:43 localhost scsi.agent[9111]:      sd_mod: loaded sucessfully

---

### Post by SteveGeorge on 2005-07-13
Looks like the kernel is seeing that you've got the disk attached fine:
> Jul 11 12:40:43 localhost kernel: Attached scsi disk sdb at scsi2, channel 0, id 0, lun 0

So the easiest way would be to make a mount point
  $ sudo mkdir /mnt/sdb1

Then mount the partition in the drive you want:
  $ sudo mount -t vfat /dev/sdb1 /mnt/sdb1

If you want the drive to automatically mount for your user when you plug it in then you need to read up on udev/hotplug/gnome-volume-manager.  The use-case for this is a user plugging in their camera and Linux automatically mounting the drive on the desktop.



Steve

---

### Post by Chongo on 2005-07-14
Thanks Steve, but I already tried mounting the drive manually and nothing happened. 

I'm not sure what the dmesg stuff means though - why does it suffer timeouts and buffer I/O errors? Someone on IRC seemed to think that it was a bug in the kernel, and so I posted it on bugzilla.

---

### Post by SteveGeorge on 2005-07-15
[QUOTE=Chongo]Thanks Steve, but I already tried mounting the drive manually and nothing happened. 

I'm not sure what the dmesg stuff means though - why does it suffer timeouts and buffer I/O errors? Someone on IRC seemed to think that it was a bug in the kernel, and so I posted it on bugzilla.[/QUOTE]
 Hmm yeah, I didn't read that bit of the thread.
Take it you've tried that drive on another machine etc.
I had a problem with ieee1394 not working on the last upgrade to my ubuntu kernel.  The only thing I could do was downgrade the kernel.
Hope you resolve it!

---

### Post by jmsa on 2005-08-23
[QUOTE=][/QUOTE]
 I have also  Lacie d2 160GB (instead of 200) USB / Firewire and the same problem as Chongo. My only solution at the moment has been to revert to a previous self-compiled 2.6.9 kernel. Ah! I also partitioned the HD with Partition Magic.

Ave atque vale.

---

### Post by grinias on 2005-08-31
I had the same problem with an external disk of 120GB which 
contains four FAT32 partitions:
```
# dmesg

Attached scsi disk sda at scsi1, channel 0, id 0, lun 0
usb-storage: device scan complete
usb 3-3: new high speed USB device using [COLOR=Red]ehci_hcd[/COLOR] and address 4
scsi2 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 4
usb-storage: waiting for device to settle before scanning
  Vendor: WDC WD12  Model: 00JB-00GVA0       Rev: 08.0
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
sda: assuming drive cache: write through
SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
sda: assuming drive cache: write through
 /dev/scsi/host2/bus0/target0/lun0

```
I had the same problem in Fedora 3 actually and I found in a forum of them that the solution is to do

```
#sudo modprobe -r ehci_hcd 
```

once you plug the disk while you are already in gnome. In that way, you remove the module

 ehci_hcd  

and the module 

 ohci_hcd
  
handles the disk automounting process:

```
#dmesg

Attached scsi disk sda at scsi2, channel 0, id 0, lun 0
usb-storage: device scan complete
ehci_hcd 0000:00:03.3: USB bus 3 deregistered
usb 1-2: new full speed USB device using [COLOR=Red]ohci_hcd[/COLOR] and address 2
usb 1-2: device descriptor read/64, error 0
scsi3 : SCSI emulation for USB Mass Storage devices
usb-storage: device found at 2
usb-storage: waiting for device to settle before scanning
  Vendor: WDC WD12  Model: 00JB-00GVA0       Rev: 08.0
  Type:   Direct-Access                      ANSI SCSI revision: 00
SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
sda: assuming drive cache: write through
SCSI device sda: 234441648 512-byte hdwr sectors (120034 MB)
sda: assuming drive cache: write through
 /dev/scsi/host3/bus0/target0/lun0: p1 p2 < p5 p6 p7 >
Attached scsi disk sda at scsi3, channel 0, id 0, lun 0
usb-storage: device scan complete
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
```

This worked for me in Ubuntu Hoary too.

---

### Post by soulglo83 on 2006-06-02
holy smokes! thank you so much, the line:

sudo modprobe -r ehci_hcd 

fixed my problem! my ipod would randomly unmount or reset, and the dmesg output was identical the first post, and many other posts i had browsed before finding this one f'ing line that apparently fixes everything for me! i don't have to goto windows anymore for anything now that i can sync my ipod w/ dapper! every day im more and more impressed by the good folks in the ubuntu community, you all rock so hard!

---

### Post by daller on 2006-06-02
I also have a mount problem in dapper... (Kubuntu)

Plugging in a harddrive in this machine, dmesg tells me this:

```

[4301040.018000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[4301040.264000] scsi2 : SCSI emulation for USB Mass Storage devices
[4301040.264000] usb-storage: device found at 2
[4301040.264000] usb-storage: waiting for device to settle before scanning
[4301045.301000]   Vendor: SAMSUNG   Model: MP0402H           Rev: UC10
[4301045.301000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4301045.306000] SCSI device sda: 78242976 512-byte hdwr sectors (40060 MB)
[4301045.306000] sda: assuming drive cache: write through
[4301045.311000] SCSI device sda: 78242976 512-byte hdwr sectors (40060 MB)
[4301045.311000] sda: assuming drive cache: write through
[4301045.311000]  sda: sda1
[4301045.747000] sd 2:0:0:0: Attached scsi disk sda
[4301045.747000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[4301045.752000] usb-storage: device scan complete

```

But the harddrive never turns up on my desktop... (on in the taskbar for that matter...) - And yes, that part is configured correctly...

Any ideas on what's wrong?

soulglo83> Did you dist-upgrade or clean-install? - It works on my clean-installed machine, but not on this one! (which i Dist-upgraded!)

---

### Post by soulglo83 on 2006-06-03
[QUOTE=daller]I also have a mount problem in dapper... (Kubuntu)

Plugging in a harddrive in this machine, dmesg tells me this:

```

[4301040.018000] usb 2-1: new full speed USB device using uhci_hcd and address 2
[4301040.264000] scsi2 : SCSI emulation for USB Mass Storage devices
[4301040.264000] usb-storage: device found at 2
[4301040.264000] usb-storage: waiting for device to settle before scanning
[4301045.301000]   Vendor: SAMSUNG   Model: MP0402H           Rev: UC10
[4301045.301000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[4301045.306000] SCSI device sda: 78242976 512-byte hdwr sectors (40060 MB)
[4301045.306000] sda: assuming drive cache: write through
[4301045.311000] SCSI device sda: 78242976 512-byte hdwr sectors (40060 MB)
[4301045.311000] sda: assuming drive cache: write through
[4301045.311000]  sda: sda1
[4301045.747000] sd 2:0:0:0: Attached scsi disk sda
[4301045.747000] sd 2:0:0:0: Attached scsi generic sg0 type 0
[4301045.752000] usb-storage: device scan complete

```

But the harddrive never turns up on my desktop... (on in the taskbar for that matter...) - And yes, that part is configured correctly...

Any ideas on what's wrong?

soulglo83> Did you dist-upgrade or clean-install? - It works on my clean-installed machine, but not on this one! (which i Dist-upgraded!)[/QUOTE]

My current install is a clean one, from dapper flight 3 and then dist-upgraded to stable.  I have however noticed that my previous installs of ubuntu, namely breezy had nearly identical dmesg and lsmod output in regard to usb storage devices.

I belive my problem comes from the combination of drive corruption on my ipod, and the ehci_hcd module panicking and unmounting.  Another kernel module i belive uhci_hcd is responsible for the automounting.  your dmesg output doesnt indicate anything unusual or different than mine, yet mine mounts!  hell w/ ehci_hcd removed the drive even unmounts completely cleanly! 

when the drive is hotplugged, is a /dev/sd* entry autopopulated?
have you tried mounting manually or via your fstab?

---

### Post by daller on 2006-06-04
I can mount it via fstab...

I have no idea of what's wrong!

Even modprobed uhci_hcd just in case...

---

### Post by soulglo83 on 2006-06-05
daller: 

i know your using a usb drive, and not an ipod, but in the context of our problems there similiar enough. with that in mind, you may want to check out this link:

[http://www.linuxquestions.org/questions/showthread.php?t=433854](http://www.linuxquestions.org/questions/showthread.php?t=433854)

as i myself have used it, and it should allow u to rig your computer so your harddrive mounts to a predictable /dev/ location, and get ubuntu to automount in the fashion you define in your /etc/fstab.  let me know if this does or doesnt help!  i literally spent nearly 20 hours trying to correct my ipod problem, and now that it works it was worth every second!

---

### Post by daller on 2006-06-05
Well, this is really weird...

Installed the package: "xfce4" some hours ago....

It magically solved this issue it seems!

---

### Post by Duffman on 2006-06-08
```
mount: wrong fs type, bad option, bad superblock on /dev/sda3,

       missing codepage or other error

       in some cases useful info is found in syslog - try

       dmesg | tail  or so



error: could not execute pmount
```

```
[4294688.670000] usb-storage: device scan complete
[4294688.808000] Driver 'sd' needs updating - please use bus_type methods
[4294688.810000] SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)[4294688.810000] sda: assuming drive cache: write through
[4294688.811000] SCSI device sda: 240121728 512-byte hdwr sectors (122942 MB)[4294688.811000] sda: assuming drive cache: write through
[4294688.811000]  sda: sda3
[4294688.827000] sd 0:0:0:0: Attached scsi disk sda
[4294688.898000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[4294688.996000] Buffer I/O error on device sda3, logical block 239607296
[4294688.996000] Buffer I/O error on device sda3, logical block 239607297
[4294688.996000] Buffer I/O error on device sda3, logical block 239607298
[4294688.996000] Buffer I/O error on device sda3, logical block 239607299

```

This is what i get when i plug in my external hd, it worked on windows...

---

### Post by Dpdk on 2006-10-07
THATS EXACTLY WHAT IS HAPPENING TO ME! Please someone figure this out. I don't want to have to go through the install of suse, I like Ubuntu but my iPod not working may force me to make the switch.

---

### Post by st4rscream on 2006-12-22
SO has anyone figured this out? I have the same error, and my partitons are hfs and unix format..

:confused: ?????:confused:

---

### Post by dannyboy79 on 2007-01-02
i have had this happen to me as well. I simply ran a fsck on the drives and then when they are reported as clean everything works again  but some people have warned me that this is a true sign that the drive is going so beware. I have backed up my drives immediately find this out as I can't afforrd to lose 250gb of avi movies. (home movies of course!)

---

### Post by kseise on 2007-06-25
I have had the same problem with the external drive just disappearing I will try 
```

sudo modprobe -r ehci_hcd 

```
as soon as I get home.  Thanks for the tip.

---

### Post by airwaffle on 2007-08-30
I just wanted to post in this thread to let people know this is still an issue. I am a complete noob, and I just installed Feisty Fawn and spent the past 3 days trying to figure out why my ipod would not automount despite the nifty UNSUAL_DEV patch. 
(found here [http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.10-rc2](http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.10-rc2))

The modprobe -r ehci_hcd command, removed whatever ehci_hcd is, and indeed, it caused the device to be deregistered from ehci_hcd and ohci_hcd took over, and it works perfectly now (automount, transfer, etc)

Thanks to everyone in this thread.

---

### Post by Tig3rzhark on 2007-12-06
$MFTMirr does not match $MFT (record 0). Failed to mount '/dev/sda1': Input/output error NTFS is either inconsistent, or you have hardware fault, or you have a SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows then reboot into Windows TWICE.  Th usage of the /f paramete is very important!  If you have SoftRAID/FakeRAID then first you must activate it and mount a different device under the /dev/mapper/ directory, (e.g. /dev/mapper/nvida_eahaabcc1).  Please see the 'dmraid' documentation for the details.

That is the error message that I get when I try to mount my external usb hard drive.  This error message started appearing after I mounted the drive during the usage of the Ubuntu Gutsy Live CD.

Does anyone have a solution to this problem?

---

### Post by jordoex on 2008-04-22
I read [this]("http://ubuntuforums.org/showthread.php?t=188802") for and external CDROM drive, so I tried it with my external hard drive, and voila! It worked!

All you have to do is plug in the usb plug before you plug in the power.  Wierd, but worked for me (I had the 'usb <...>: device descriptor read/64, error -110' problem), and it might work for some of you.  I also used 'modprobe -r echi' and 'modprobe -r ochi', which might have helped.

My hard drive stopped working on linux after I repartitioned it cuz FAT has the 4 gig filesize limit.

---

