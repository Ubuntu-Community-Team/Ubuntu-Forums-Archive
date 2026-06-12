---
title: "External USB SATA Hard Drive not functioning"
date: 2008-08-23
forum: Hardware
---

### Post by HarrisonBP on 2008-08-23
Well, I am new to linux, and I still have all of "My Documents" on my External USB SATA Hard Drive because I can't seem to get them transfered.  

Please help if you can.

---

### Post by HarrisonBP on 2008-08-23
Sorry to bump, but I am anxious.  I have continued to search for an answer, but to no avail.

---

### Post by coffeecat on 2008-08-23
You don't say what you've done, but I'm guessing that you've plugged the USB drive in, switched it on and nothing has happened. As you are talking about 'My Documents' I assume you are coming from the Windows world and the external USB drive will be formatted with either the FAT32 or NTFS filesystems. Both should work read-write out of the box with Ubuntu Hardy 8.04. What should happen a few seconds after you switch on the drive is that an icon will appear on your desktop **and** a file manager window will open. In the Gnome desktop of Ubuntu, this is called Nautilus. It's equivalent to Windows Explorer and functionally very similar.

So I assume that you haven't seen either a desktop icon or a browser window. If so, something is wrong.

First - can you confirm what the filesystem is on the USB drive? Is it still readable in Windows?

Second - you have a SATA USB drive. I have two of these and I have twice been caught out by a simple gotcha. There will probably be a switch on it, USB2.0 and ESATA. If you've accidentally switched it to ESATA (easily done) it won't get mounted when you plug it in. This is true of Windows and MacOS as well. Check that the switch is switched to USB.

Third - which version of Ubuntu are you using? If you are using a version earlier than 8.04 (Hardy Heron) you may not get read-write with NTFS but the drive should still be mounted at least read only - as far as I remember. If it's FAT32 you should have no problem at all.

I'm afraid you won't get another post out of me for at least 8 hours. It's gone midnight here and I'm signing off now.

Good luck.

---

### Post by HarrisonBP on 2008-08-23
It does not look like ubuntu sees my HDD, no desktop icon or window.  

I have FAT32 filesystem, I think.

There is only a usb port on my drive, no switch or ESATA.

I am using 8.04.

Maybe some other nice forumophyle (or foruphyle, which) can help me before the morn.

Thanks

---

### Post by libra1780 on 2008-08-23
could be that it's only not mounted

open the console and type
```

ls /dev/sd*

```

your output should be something like this
```

/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdb1  /dev/sdb2

```

here sda is a hd, sda1,sda2 and sda3 are its partitions
now type
```

mount | grep sd

```
check whitch partition is missing and mount it, fo ex. sde1
if there is no partition listed use the disks label (ex. sde) instead

```

sudo mount /dev/sde1 /mnt -t vfat -o user,exec,umask=000,rw

```

should be right *g* got no fat32 around to test it
now you have your disk mounted read/write and you find it in the /mnt folder

type (ex)
```

sudo umount /dev/sde1

```
to unmount

---

### Post by HarrisonBP on 2008-08-24
> **libra1780 said:**
> could be that it's only not mounted

open the console and type
```

ls /dev/sd*

```

your output should be something like this
```

/dev/sda  /dev/sda1  /dev/sda2  /dev/sda3  /dev/sdb  /dev/sdb1  /dev/sdb2

```




My output is:

harrison@harrison-laptop:~$ ls /dev/sd*
ls: cannot access /dev/sd*: No such file or directory

---

### Post by HarrisonBP on 2008-08-24
bump

---

### Post by forger on 2008-08-24
Can you post the output of these commands too:
```

sudo apt-get update
sudo apt-get upgrade
lspci
lsusb

```
(you will be asked to type your password at the first command)

Then execute these:
```
sudo update-pciids
sudo update-usbids
```

Then reboot your machine, and try it again:
```

lspci
lsusb

```
Post the results once more

---

### Post by HarrisonBP on 2008-08-24
harrison@harrison-laptop:~$ sudo apt-get update
[sudo] password for harrison:
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy Release.gpg
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy/main Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy/restricted Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy/universe Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy/multiverse Translation-en_US
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-updates Release.gpg
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-updates/main Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-updates/restricted Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-updates/universe Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-updates/multiverse Translation-en_US
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-security Release.gpg
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-security/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release.gpg
Hit [http://dl.google.com](http://dl.google.com) stable Release.gpg
Ign [http://dl.google.com](http://dl.google.com) stable/non-free Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release.gpg
Ign [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-security/restricted Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-security/universe Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-security/multiverse Translation-en_US
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-backports Release.gpg
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-backports/restricted Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-backports/main Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-backports/multiverse Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-backports/universe Translation-en_US
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-proposed Release.gpg
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-proposed/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy Release
Hit [http://dl.google.com](http://dl.google.com) stable Release
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-proposed/main Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-proposed/multiverse Translation-en_US
Ign [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-proposed/universe Translation-en_US
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy Release
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-updates Release
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-security Release
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-backports Release
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-proposed Release
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy Release
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Packages
Hit [http://dl.google.com](http://dl.google.com) stable/non-free Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy/restricted Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy/universe Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy/multiverse Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-updates/main Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-updates/restricted Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-updates/universe Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-updates/multiverse Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) hardy/partner Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-security/main Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-security/restricted Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-security/universe Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-security/multiverse Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-backports/restricted Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-backports/main Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-backports/multiverse Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-backports/universe Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-proposed/restricted Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-proposed/main Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-proposed/multiverse Packages
Hit [http://mirror.cc.columbia.edu](http://mirror.cc.columbia.edu) hardy-proposed/universe Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
Reading package lists... Done
harrison@harrison-laptop:~$
harrison@harrison-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
harrison@harrison-laptop:~$ lspci
00:00.0 Host bridge: ALi Corporation M1672 Northbridge [CyberALADDiN-P4]
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 USB Controller: NEC Corporation USB (rev 43)
00:0c.1 USB Controller: NEC Corporation USB (rev 43)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:10.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
harrison@harrison-laptop:~$ lsusb
Bus 003 Device 010: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1241:1166 Belkin optical mouse w/ scrollwheel
Bus 001 Device 001: ID 0000:0000
harrison@harrison-laptop:~$ sudo update-pciids
--17:49:10--  [http://pciids.sourceforge.net/v2.2/pci.ids.bz2](http://pciids.sourceforge.net/v2.2/pci.ids.bz2)
           => `/usr/share/misc/pci.ids.gz.new'
Resolving pciids.sourceforge.net... 66.35.250.209
Connecting to pciids.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 133,875 (131K) [text/plain]

100%[====================================>] 133,875      110.88K/s

17:49:12 (110.79 KB/s) - `/usr/share/misc/pci.ids.gz.new' saved [133875/133875]

Done.
harrison@harrison-laptop:~$ sudo update-usbids
--17:49:36--  [http://linux-usb.sourceforge.net/usb.ids](http://linux-usb.sourceforge.net/usb.ids)
           => `/var/lib/misc/usb.ids.new'
Resolving linux-usb.sourceforge.net... 66.35.250.209
Connecting to linux-usb.sourceforge.net|66.35.250.209|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 353,550 (345K) [text/plain]

100%[====================================>] 353,550       95.59K/s    ETA 00:00

17:49:40 (95.42 KB/s) - `/var/lib/misc/usb.ids.new' saved [353550/353550]

Done.








Rebooting now.

---

### Post by HarrisonBP on 2008-08-24
After reboot, I get this:


00:00.0 Host bridge: ALi Corporation M1672 Northbridge [CyberALADDiN-P4]
00:01.0 PCI bridge: ALi Corporation PCI to AGP Controller
00:04.0 IDE interface: ALi Corporation M5229 IDE (rev c4)
00:06.0 Multimedia audio controller: ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)
00:07.0 ISA bridge: ALi Corporation M1533/M1535 PCI to ISA Bridge [Aladdin IV/V/V+]
00:08.0 Bridge: ALi Corporation M7101 Power Management Controller [PMU]
00:09.0 Modem: ALi Corporation M5457 AC'97 Modem Controller
00:0a.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:0c.0 USB Controller: NEC Corporation USB (rev 43)
00:0c.1 USB Controller: NEC Corporation USB (rev 43)
00:0c.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
00:10.0 Ethernet controller: Atheros Communications Inc. AR5212/AR5213 Multiprotocol MAC/baseband processor (rev 01)
00:11.0 CardBus bridge: Toshiba America Info Systems ToPIC100 PCI to Cardbus Bridge with ZV Support (rev 33)
00:12.0 System peripheral: Toshiba America Info Systems SD TypA Controller (rev 05)
01:00.0 VGA compatible controller: Trident Microsystems CyberBlade XPAi1 (rev 82)
harrison@harrison-laptop:~$ lsusb
Bus 003 Device 003: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 003: ID 1241:1166 Belkin MI-2150 Trust Mouse
Bus 001 Device 001: ID 0000:0000
harrison@harrison-laptop:~$        



So, after the reboot, I now can see a USB drive in my file browser, but when I try to doubleclick on it, it says

"Unable to mount location.

"Can't mount file."

But we're getting there.

---

### Post by forger on 2008-08-24
1) head to System > administration > hardware drivers - see if there are any drivers not checked and check them so they'll be installed.
(Reboot if asked to)

2) Is the hard drive ntfs or fat32?

3) post the output of these:
```
sudo fdisk -l
ls /dev/sd*
ls -l /dev/disk/by-id
```

---

### Post by HarrisonBP on 2008-08-24
1) All drivers (both for LAN) are checked

2) My brother tells me it is a FAT 32

3) 

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xee05ee05

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9364    75216298+  83  Linux
/dev/hda2            9365        9729     2931862+   5  Extended
/dev/hda5            9365        9729     2931831   82  Linux swap / Solaris
harrison@harrison-laptop:~$ ls /dev/sd*
ls: cannot access /dev/sd*: No such file or directory
harrison@harrison-laptop:~$
harrison@harrison-laptop:~$ ls -l /dev/disk/by-id
total 0
lrwxrwxrwx 1 root root  9 2008-08-24 17:52 ata-IC25N080ATMR04-0_MRG4D4K4GNBBHS -> ../../hda
lrwxrwxrwx 1 root root 10 2008-08-24 17:52 ata-IC25N080ATMR04-0_MRG4D4K4GNBBHS-part1 -> ../../hda1
lrwxrwxrwx 1 root root 10 2008-08-24 17:52 ata-IC25N080ATMR04-0_MRG4D4K4GNBBHS-part2 -> ../../hda2
lrwxrwxrwx 1 root root 10 2008-08-24 17:52 ata-IC25N080ATMR04-0_MRG4D4K4GNBBHS-part5 -> ../../hda5
lrwxrwxrwx 1 root root  9 2008-08-24 17:52 ata-TOSHIBA_DVD-ROM_SD-R2412_Z346020308 -> ../../hdc
harrison@harrison-laptop:~$

---

### Post by forger on 2008-08-24
hd*.. interesting, I thought ubuntu had switched everything to sd* :)
Well from the looks of it, you only have a dvd and a hitachi 80gb hard drive, your usb drive wasn't detected normally.

Ok, do this:
- shutdown ubuntu
- wait for 30 seconds or so, unplug and then shut down the hard drive
- start your computer again
- log in
- wait to load completely, then start and plug in your hard drive, wait for 15 seconds
- post the result of this command:
```
dmesg | tail -n 40
```

By the way, is it really an external drive or is it a normal internal hard drive in an external case? What brand/model is it?

---

### Post by dsm iv tr on 2008-08-24
If it's fat32, make sure the vfat module is loaded before you try to mount it, assuming it's detected properly by the kernel.

```

sudo modprobe fat32

```

---

### Post by HarrisonBP on 2008-08-24
I'll restart in a sec.  Good call on the drive though, yes it is an internal laptop drive in an external case, It's actuall my brother's, and he's taking a nap right now.  (Lazy law students) But I know it's out of a Lenovo Thinkpad, about 2 yr. old.

Also, 

harrison@harrison-laptop:~$ sudo modprobe fat32
FATAL: Module fat32 not found.

But I'll still try the reboot.

---

### Post by forger on 2008-08-24
the module is actually *vfat* :)
```
sudo modprobe -v vfat
```

---

### Post by HarrisonBP on 2008-08-24
[   44.505389] Bluetooth: RFCOMM TTY layer initialized
[   44.505390] Bluetooth: RFCOMM ver 1.8
[   65.660397] NET: Registered protocol family 10
[   65.660757] lo: Disabled Privacy Extensions
[   65.661286] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   76.286826] ath0: no IPv6 routers present
[   81.085133] NET: Registered protocol family 17
[  100.220508] ath0: no IPv6 routers present
[  256.318528] usb 3-3: new high speed USB device using ehci_hcd and address 3
[  256.452979] usb 3-3: configuration #1 chosen from 1 choice
[  256.570049] usbcore: registered new interface driver libusual
[  256.633168] Initializing USB Mass Storage driver...
[  256.639805] scsi0 : SCSI emulation for USB Mass Storage devices
[  256.641760] usbcore: registered new interface driver usb-storage
[  256.641772] USB Mass Storage support registered.
[  256.645896] usb-storage: device found at 3
[  256.645904] usb-storage: waiting for device to settle before scanning
[  261.643111] usb-storage: device scan complete
[  261.644088] scsi 0:0:0:0: Direct-Access     FUJITSU  MHV2060BH        0028 PQ: 0 ANSI: 2 CCS
[  261.832675] Driver 'sd' needs updating - please use bus_type methods
[  261.834716] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[  261.835992] sd 0:0:0:0: [sda] Write Protect is off
[  261.836001] sd 0:0:0:0: [sda] Mode Sense: 00 38 00 00
[  261.836004] sd 0:0:0:0: [sda] Assuming drive cache: write through
[  261.837228] sd 0:0:0:0: [sda] 117210240 512-byte hardware sectors (60012 MB)
[  261.837978] sd 0:0:0:0: [sda] Write Protect is off
[  261.837985] sd 0:0:0:0: [sda] Mode Sense: 00 38 00 00
[  261.837988] sd 0:0:0:0: [sda] Assuming drive cache: write through
[  261.837995]  sda: sda1 sda2
[  261.864018] sd 0:0:0:0: [sda] Attached SCSI disk
[  261.914674] sd 0:0:0:0: Attached scsi generic sg0 type 0
[  292.218069] usb 3-3: reset high speed USB device using ehci_hcd and address 3
[  302.463754] usb 3-3: reset high speed USB device using ehci_hcd and address 3
harrison@harrison-laptop:~$


Also, now places > computer does not show my usb drive

---

### Post by HarrisonBP on 2008-08-24
now I get this

harrison@harrison-laptop:~$ sudo modprobe -v vfat
[sudo] password for harrison:
insmod /lib/modules/2.6.24-21-generic/kernel/fs/fat/fat.ko
insmod /lib/modules/2.6.24-21-generic/kernel/fs/vfat/vfat.ko
harrison@harrison-laptop:~$

---

### Post by HarrisonBP on 2008-08-24
Also, now my filesystem does not recognize my drive anymore.

---

### Post by HarrisonBP on 2008-08-25
bump

---

### Post by dsm iv tr on 2008-08-25
> **forger said:**
> the module is actually *vfat* :)
```
sudo modprobe -v vfat
```

Haha, oops. I even named it right in my post and I mistyped it! D'oh!

Thanks, forger.

---

### Post by dsm iv tr on 2008-08-25
It occurs to me I just had nearly the same problem with my external drive connecting via USB. It would be detected, and then it wouldn't mount. Any access to it would cause the bus to send resets, just like yours! I then noticed people were having issues with ehci-hcd (the USB2 480mbps module) and I tried disabling it. There is apparently a fix upstream for the issue if you poke around, too, but I didn't care to upgrade because I haven't made a backup yet of the working config.

You can try this, if you want:

[http://ubuntuforums.org/showpost.php?p=5617795&postcount=10](http://ubuntuforums.org/showpost.php?p=5617795&postcount=10)

It causes all usb devices on the bus to run at 12mbps instead, but at least they work. Note that you can easily reverse any changes you make with it just by copying the module back, rebuilding the initramfs, and removing the "blacklist" line. I think a kernel upgrade will also wipe out the fix - but hopefully by that time the issue will be patched.

---

### Post by forger on 2008-08-25
If what dsm iv tr suggests doesn't work, unblacklist the module and reboot (so you'll be back to normal). Then I would shut down the computer, take out the hard drive and try to connect it from a normal SATA (not usb), just to see if it's working normally under its physical circumstances.
Does it work in other operating systems, like opensuse or windows xp?

---

### Post by supi007 on 2009-11-07
My problem is the same. I have got a SATA HD and this is brand new without any partition table. I have got a notebook which has got USB interface. A I have got an HDD adapter (SATA-ATA-USB) and I would like to use the new HD under UBUNTU.
I have switched on the HD after I've pluged into the USB then I've started the system.
After I got this -->

```

user@nb09ulx0321sb:~$ sudo fdisk -l
[sudo] password for bsapi: 

/dev/sda disk: 160.0 GB, 160041885696 byte
255 head, 63 sector, 19457 cylinder
Egység: cylinders 16065 * 512 = 8225280 byte
Disk ID: 0xc0492a6b

  Device Boot   Start         End      Blocks  Az  System
/dev/sda1   *           2       18437   148087138+   7  HPFS/NTFS
/dev/sda2           18438       19422     7912012+  83  Linux
/dev/sda3           19423       19457      281137+  82  Linux lapozó / Solaris

/dev/sdb disk: 2199.0 GB, 2199023255552 byte
255 head, 63 sector, 267349 cylinder
Egység: cilinderek 16065 * 512 = 8225280 byte
Disk ID: 0xc020c020

A(z) /dev/sdb lemez nem tartalmaz érvényes partíciós táblát

```
The sda is my internal HD. Okay.
The sdb is the external HD, but this is not 2 TiB (unfortunately) because only 320GiB.
What can I do than I want to use it? Any proposal?
Thanks in advance.

supesz

:KS

---

### Post by supi007 on 2009-11-07
This is my HD in numbers:

HD322HJ                       
Number of disks          1 
                      Number of read/write heads          2                       
Logical cylinders          16,383                       
Logical heads          16                       
Logical sectors/track          63                       
Bytes per sector          1024                       
Target Mumber of LBAs          625,142,448

any proposal how can I fit it to my Ubuntu?

supesz

---

