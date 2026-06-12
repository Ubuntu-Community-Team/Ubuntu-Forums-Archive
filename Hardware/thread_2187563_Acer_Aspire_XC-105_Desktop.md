---
title: "Acer Aspire XC-105 Desktop"
date: 2013-11-12
forum: Hardware
---

### Post by AndyGaskell on 2013-11-12
Hi

I've just bought a new PC, to use as a HTPC and SVN server to replace my old ASRock ION-330. It is a Acer Aspire XC-105 Desktop, which are going for £160 on eBuyer at the moment.

So, I've been trying to get Ubuntu on it, and have had no luck.  I was just wondering if anyone else has this model and had any success with it.  What I've tried so far is installing from "ubuntu-12.04.3-desktop-amd64.iso", "ubuntu-13.10-desktop-amd64.iso" and "mini_ubuntu-13.10-desktop-amd64.iso".   I know it's key to give good details on what errors occur, but in this case it is quite dificult, as it varies a little.  In most instances it says it has installed ok, but on first boot it just hangs after about 15 seconds, just dropping to a flashing cursor, at which you can't type anything.  Can't find too much useful stuff on Google, probably as this is a new Acer system.  I'll keep looking into it here, and any progress I find I'll add here for future googlers.

The specs...
AMD A4-5000
1.5GHz
4GB RAM
500GB HDD
DVD ROM
AMD HD8330

Some helpful links...

The product page on eBuyer...
[http://www.ebuyer.com/567280-acer-aspire-xc-105-desktop-dt-sr4ek-013](http://www.ebuyer.com/567280-acer-aspire-xc-105-desktop-dt-sr4ek-013)

There is some chat related to this at...
[https://forums.ebuyer.com/showthread.php/80643-Acer-Aspire-XC-105-Desktop](https://forums.ebuyer.com/showthread.php/80643-Acer-Aspire-XC-105-Desktop)
...and at...
[http://forum.xbmc.org/showthread.php?tid=176201](http://forum.xbmc.org/showthread.php?tid=176201)

Some background on the CPU / APU / System...
[http://techreport.com/review/24856/amd-a4-5000-kabini-apu-reviewed](http://techreport.com/review/24856/amd-a4-5000-kabini-apu-reviewed)

---

### Post by AndyGaskell on 2013-11-15
Further to the first post, I've tried a few more options, like xubuntu-13.10-desktop-amd64 and have had no more luck.  I do have a clearer idea of how to describe the issue though. Booting a USB drive with xubuntu-13.10-desktop-amd64, then, on boot choosing the "Try Ubuntu" option.  It starts booting up, and then stops.  The screen it stops at is shown below.

[IMG]http://www.ssofb.co.uk/uploads/Acer_Aspire_XC-105_screen.jpg[/IMG]

---

### Post by TDave on 2013-11-18
Had a similar issue here, although my basic scenario was as follows:

1. USB booted (ubuntu-13.10-desktop-amd64), went straight to "Install Ubuntu" as I was (overly) confident it would run just fine
2. Failed to check what the partition manager was doing, and just let it do it's thing advising it to remove FreeDOS completely and stick Ubuntu on the entire drive using LVM
3. Install ticks over, I go away and watch TV for a bit
4. Come back, install's finished, reboot and remove USB
5. FreeDOS boots (err....)

My biggest bug-bear at this point was that now the USB drive stopped being bootable. It started, then fell apart with a Kernel error. My assumption was that somewhere along the lines the auto-magic partition had bust something, but that is pure speculation and not something I looked into in too much detail.
Another idea was that EFI was screwing around, so I messed with the settings a bit but to no avail.

I did, however, end up getting Ubuntu booting, albeit minimally, by going back to an earlier method of installing it - the mini.iso ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD))

Downloaded the latest amd64 mini.iso, used unetbootin to stick it on my USB drive and got it booted. The install was straightforward (obviously helps if you've seen the text-based installer before) and following a reboot the system booted straight to the command prompt, as expected (no sign of FreeDOS!). Being the mini.iso and to save more messing around, I just booted "legacy" MBR rather than UEFI but at least it was booting.

Had a quick check of lspci (I'll paste the output later, didn't grab a copy at the time, and nothing particularly looked untoward so I went ahead and "apt-get install ubuntu-desktop".
Install ran through and I rebooted. However, the boot got as far as starting to load the Desktop / Login Manager when a pop-up window informed me it was going to run in Low Graphics mode. Clicking ok dropped me back out to the CLI.

Didn't have any chance to look into it further over the weekend but I'll have a look later on, so far my suspicions are:
1. The integrated graphics are too new for the available drivers (need to check exactly what will be needed to make sure it's not available-but-not-installed). I might also check this by trying to live-boot something Arch-based or similarly "bleeding edge"
2. The platform in general just isn't supported at present in Ubuntu / Linux
3. Something else entirely (I'm no expert!)

---

### Post by AndyGaskell on 2013-11-18
Hi TDave

That's great you made some progress.  Thanks for adding your notes.  Good that Ubuntu minimal worked, and interesting that it went pear shaped with the desktop bit.  That'd suggest an issue with the integrated graphics drivers / set-up I'd guess.

The suspicions you mentioned are pretty much what I was thinking.  I played with some of the EFI settings too and that didn't make any difference.

I also tried Linux Mint (linuxmint-15-xfce-dvd-64bit) and that got a proper kernel panic on install, with flashing keyboard lights etc.  The message was as follows...
[IMG]http://www.ssofb.co.uk/uploads/Acer_Aspire_XC-105_screen_mint.jpg[/IMG]

Then I tried Fedora (Fedora-19-x86_64-DVD), to see if it did anything useful or gave any clues.  This also crashed out during install, though it did give some semi-useful messages...
[IMG]http://www.ssofb.co.uk/uploads/Acer_Aspire_XC-105_screen_fedora.jpg[/IMG]

The only thing I got running on it was Knoppix (KNOPPIX_V7.2.0DVD-2013-06-16-EN), but that is not so useful generally, though a good test case.

I'll try minimal ubuntu again.

---

### Post by TDave on 2013-11-18
Yep, that kernel error is the same one I was getting every time I tried to boot from the USB stick after the first "install". Never had it once I rewrote the USB stick with the mini.iso though.

My aim is to have a more detailed play with it when I get in later, so I'll update this accordingly. Hopefully someone can spot something I can't!

---

### Post by AndyGaskell on 2013-11-18
Hi TD
Good to not be alone on this one, it seems a great wee bargain PC, so it'll be good to sort out these issues for Linux.  I'll try Knoppix again and paste in lspci into this thread.

---

### Post by AndyGaskell on 2013-11-18
I fired up Knoppix (KNOPPIX_V7.2.0DVD-2013-06-16-EN) on the system again. It seems odd that Knoppix works, as that is Debian based like Ubuntu, and is also an older kernel.

Some hopefully useful output from knoppix...

uname -a
Linux Microknoppix 3.9.6-64 #23 SMP PREEMPT Sat Jun 15 14:15:39 CEST 2013 x86_64 GNU/Linux

lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Device 9832
00:01.1 Audio device: Advanced Micro Devices [AMD] nee ATI Device 9840
00:02.0 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 0
00:02.5 PCI bridge: Advanced Micro Devices [AMD] Family 16h Processor Functions 5:1
00:10.0 USB controller: Advanced Micro Devices [AMD] FCH USB XHCI Controller (rev 01)
00:11.0 SATA controller: Advanced Micro Devices [AMD] FCH SATA Controller [IDE mode] (rev 40)
00:12.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 39)
00:12.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 39)
00:13.0 USB controller: Advanced Micro Devices [AMD] FCH USB OHCI Controller (rev 39)
00:13.2 USB controller: Advanced Micro Devices [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices [AMD] Family 16h Processor Function 5
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 11)

lsusb
Bus 001 Device 003: ID 05dc:a815 Lexar Media, Inc.
Bus 002 Device 002: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 003 Device 002: ID 04f2:0833 Chicony Electronics Co., Ltd
Bus 003 Device 003: ID 192f:0616 Avago Technologies, Pte.
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub

dmesg
[ 2.620641] usb usb6: New USB device found, idVendor=1d6b, idProduct=0003
[ 2.620646] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[ 2.620650] usb usb6: Product: xHCI Host Controller
[ 2.620655] usb usb6: Manufacturer: Linux 3.9.6-64 xhci_hcd
[ 2.620659] usb usb6: SerialNumber: 0000:00:10.0
[ 2.620861] xHCI xhci_add_endpoint called for root hub
[ 2.620864] xHCI xhci_check_bandwidth called for root hub
[ 2.620995] hub 6-0:1.0: USB hub found
[ 2.621007] hub 6-0:1.0: 2 ports detected
[ 2.642066] Initializing USB Mass Storage driver...
[ 2.642204] usbcore: registered new interface driver usb-storage
[ 2.642208] USB Mass Storage support registered.
[ 2.642294] usbcore: registered new interface driver ums-alauda
[ 2.642383] usbcore: registered new interface driver ums-cypress
[ 2.642469] usbcore: registered new interface driver ums-datafab
[ 2.642556] usbcore: registered new interface driver ums_eneub6250
[ 2.642637] usbcore: registered new interface driver ums-freecom
[ 2.642721] usbcore: registered new interface driver ums-isd200
[ 2.642803] usbcore: registered new interface driver ums-jumpshot
[ 2.642884] usbcore: registered new interface driver ums-karma
[ 2.642966] usbcore: registered new interface driver ums-onetouch
[ 2.643056] usbcore: registered new interface driver ums-realtek
[ 2.643138] usbcore: registered new interface driver ums-sddr09
[ 2.643222] usbcore: registered new interface driver ums-sddr55
[ 2.643304] usbcore: registered new interface driver ums-usbat
[ 2.643621] i8042: PNP: No PS/2 controller found. Probing ports directly.
[ 2.644116] serio: i8042 KBD port at 0x60,0x64 irq 1
[ 2.644178] serio: i8042 AUX port at 0x60,0x64 irq 12
[ 2.644525] mousedev: PS/2 mouse device common for all mice
[ 2.645061] rtc_cmos 00:06: RTC can wake from S4
[ 2.645255] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[ 2.645289] rtc_cmos 00:06: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[ 2.645407] device-mapper: uevent: version 1.0.3
[ 2.645538] device-mapper: ioctl: 4.24.0-ioctl (2013-01-15) initialised: [email]dm-devel@redhat.com[/email]
[ 2.645659] cpuidle: using governor ladder
[ 2.645798] cpuidle: using governor menu
[ 2.645880] sdhci: Secure Digital Host Controller Interface driver
[ 2.645883] sdhci: Copyright(c) Pierre Ossman
[ 2.646248] wbsd: Winbond W83L51xD SD/MMC card interface driver
[ 2.646251] wbsd: Copyright(c) Pierre Ossman
[ 2.646599] VUB300 Driver rom wait states = 1C irqpoll timeout = 0400
[ 2.646837] usbcore: registered new interface driver vub300
[ 2.646928] usbcore: registered new interface driver ushc
[ 2.647016] sdhci-pltfm: SDHCI platform and OF driver helper
[ 2.647259] hidraw: raw HID events driver (C) Jiri Kosina
[ 2.649477] usbcore: registered new interface driver usbhid
[ 2.649480] usbhid: USB HID core driver
[ 2.649575] usbcore: registered new interface driver rts5139
[ 2.649920] zram: Created 1 device(s) ...
[ 2.650233] ashmem: initialized
[ 2.650405] AMD IOMMUv2 driver by Joerg Roedel <joerg.roedel@amd.com>
[ 2.650409] AMD IOMMUv2 functionality not available on this system
[ 2.651246] Initializing XFRM netlink socket
[ 2.651260] NET: Registered protocol family 17
[ 2.651278] NET: Registered protocol family 15
[ 2.651568] Key type dns_resolver registered
[ 2.652068] registered taskstats version 1
[ 2.652553] rtc_cmos 00:06: setting system clock to 2013-11-18 20:24:20 UTC (1384806260)
[ 2.652819] acpi-cpufreq: overriding BIOS provided _PSD data
[ 2.653499] ALSA device list:
[ 2.653503] No soundcards found.
[ 2.655836] Freeing unused kernel memory: 900k freed
[ 2.656161] Write protecting the kernel read-only data: 12288k
[ 2.661915] Freeing unused kernel memory: 800k freed
[ 2.670457] Freeing unused kernel memory: 1272k freed
[ 2.851826] usb 1-3: new high-speed USB device number 3 using ehci-pci
[ 3.243524] FAT-fs (sda): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 3.281326] UDF-fs: warning (device sda): udf_fill_super: No partition found (1)
[ 3.284173] F2FS-fs (sda): Magic Mismatch, valid(0xf2f52010) - read(0xc12a7328)
[ 3.284183] F2FS-fs (sda): Can't find a valid F2FS filesystem in first superblock
[ 3.284418] F2FS-fs (sda): Magic Mismatch, valid(0xf2f52010) - read(0x0)
[ 3.284429] F2FS-fs (sda): Can't find a valid F2FS filesystem in second superblock
[ 3.286355] FAT-fs (sda1): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 3.310901] FAT-fs (sda1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[ 3.314828] FAT-fs (sda2): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 3.431581] usb 1-3: New USB device found, idVendor=05dc, idProduct=a815
[ 3.431590] usb 1-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3.431596] usb 1-3: Product: USB Flash Drive
[ 3.431600] usb 1-3: Manufacturer: Lexar
[ 3.431605] usb 1-3: SerialNumber: AA2YLZB4KK81GOZK
[ 3.432323] scsi4 : usb-storage 1-3:1.0
[ 3.449254] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[ 3.460776] FAT-fs (sda3): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 3.535472] UDF-fs: warning (device sda3): udf_fill_super: No partition found (1)
[ 3.538219] F2FS-fs (sda3): Magic Mismatch, valid(0xf2f52010) - read(0x1)
[ 3.538230] F2FS-fs (sda3): Can't find a valid F2FS filesystem in first superblock
[ 3.538495] F2FS-fs (sda3): Magic Mismatch, valid(0xf2f52010) - read(0x4c3842)
[ 3.538505] F2FS-fs (sda3): Can't find a valid F2FS filesystem in second superblock
[ 3.831966] usb 2-3: new high-speed USB device number 2 using ehci-pci
[ 3.958459] usb 2-3: New USB device found, idVendor=058f, idProduct=6366
[ 3.958477] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 3.958488] usb 2-3: Product: Flash Card Reader/Writer
[ 3.958497] usb 2-3: Manufacturer: Generic
[ 3.958506] usb 2-3: SerialNumber: 058F63666485
[ 3.960217] scsi5 : usb-storage 2-3:1.0
[ 4.088658] usb 3-2: new low-speed USB device number 2 using ohci_hcd
[ 4.251458] usb 3-2: New USB device found, idVendor=04f2, idProduct=0833
[ 4.251476] usb 3-2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[ 4.251487] usb 3-2: Product: USB Keyboard
[ 4.251495] usb 3-2: Manufacturer: CHICONY
[ 4.260621] input: CHICONY USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.0/input/input2
[ 4.261115] hid-generic 0003:04F2:0833.0001: input,hidraw0: USB HID v1.00 Keyboard [CHICONY USB Keyboard] on usb-0000:00:12.0-2/input0
[ 4.276688] input: CHICONY USB Keyboard as /devices/pci0000:00/0000:00:12.0/usb3/3-2/3-2:1.1/input/input3
[ 4.277518] hid-generic 0003:04F2:0833.0002: input,hiddev0,hidraw1: USB HID v1.00 Device [CHICONY USB Keyboard] on usb-0000:00:12.0-2/input1
[ 4.525374] usb 3-4: new low-speed USB device number 3 using ohci_hcd
[ 4.681331] usb 3-4: New USB device found, idVendor=192f, idProduct=0616
[ 4.681348] usb 3-4: New USB device strings: Mfr=0, Product=2, SerialNumber=0
[ 4.681359] usb 3-4: Product: USB Optical Mouse
[ 4.689577] input: USB Optical Mouse as /devices/pci0000:00/0000:00:12.0/usb3/3-4/3-4:1.0/input/input4
[ 4.690228] hid-generic 0003:192F:0616.0003: input,hidraw2: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:12.0-4/input0
[ 4.963340] scsi 5:0:0:0: Direct-Access Multiple Card Reader 1.00 PQ: 0 ANSI: 4
[ 4.964698] sd 5:0:0:0: Attached scsi generic sg2 type 0
[ 4.966797] sd 5:0:0:0: [sdb] Attached SCSI removable disk
[ 6.071076] FAT-fs (sda): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 6.122971] UDF-fs: warning (device sda): udf_fill_super: No partition found (1)
[ 6.125562] F2FS-fs (sda): Magic Mismatch, valid(0xf2f52010) - read(0xc12a7328)
[ 6.125572] F2FS-fs (sda): Can't find a valid F2FS filesystem in first superblock
[ 6.125798] F2FS-fs (sda): Magic Mismatch, valid(0xf2f52010) - read(0x0)
[ 6.125808] F2FS-fs (sda): Can't find a valid F2FS filesystem in second superblock
[ 6.127709] FAT-fs (sda1): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 6.129474] FAT-fs (sda1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[ 6.132655] FAT-fs (sda2): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 6.221262] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[ 6.230942] FAT-fs (sda3): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 6.264995] UDF-fs: warning (device sda3): udf_fill_super: No partition found (1)
[ 6.267695] F2FS-fs (sda3): Magic Mismatch, valid(0xf2f52010) - read(0x1)
[ 6.267706] F2FS-fs (sda3): Can't find a valid F2FS filesystem in first superblock
[ 6.267935] F2FS-fs (sda3): Magic Mismatch, valid(0xf2f52010) - read(0x4c3842)
[ 6.267946] F2FS-fs (sda3): Can't find a valid F2FS filesystem in second superblock
[ 6.470561] scsi 4:0:0:0: Direct-Access Lexar USB Flash Drive 1100 PQ: 0 ANSI: 4
[ 6.472151] sd 4:0:0:0: Attached scsi generic sg3 type 0
[ 6.473071] sd 4:0:0:0: [sdc] 15384576 512-byte logical blocks: (7.87 GB/7.33 GiB)
[ 6.474067] sd 4:0:0:0: [sdc] Write Protect is off
[ 6.474080] sd 4:0:0:0: [sdc] Mode Sense: 43 00 00 00
[ 6.475097] sd 4:0:0:0: [sdc] No Caching mode page present
[ 6.475110] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 6.479844] sd 4:0:0:0: [sdc] No Caching mode page present
[ 6.479856] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 6.481085] sdc: sdc1
[ 6.484813] sd 4:0:0:0: [sdc] No Caching mode page present
[ 6.484824] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[ 6.484834] sd 4:0:0:0: [sdc] Attached SCSI removable disk
[ 8.801528] FAT-fs (sda): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 8.853432] UDF-fs: warning (device sda): udf_fill_super: No partition found (1)
[ 8.856517] F2FS-fs (sda): Magic Mismatch, valid(0xf2f52010) - read(0xc12a7328)
[ 8.856528] F2FS-fs (sda): Can't find a valid F2FS filesystem in first superblock
[ 8.856740] F2FS-fs (sda): Magic Mismatch, valid(0xf2f52010) - read(0x0)
[ 8.856749] F2FS-fs (sda): Can't find a valid F2FS filesystem in second superblock
[ 8.858902] FAT-fs (sdc): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 8.967590] UDF-fs: warning (device sdc): udf_fill_super: No partition found (1)
[ 8.972912] F2FS-fs (sdc): Magic Mismatch, valid(0xf2f52010) - read(0x0)
[ 8.972923] F2FS-fs (sdc): Can't find a valid F2FS filesystem in first superblock
[ 8.973820] F2FS-fs (sdc): Magic Mismatch, valid(0xf2f52010) - read(0x0)
[ 8.973830] F2FS-fs (sdc): Can't find a valid F2FS filesystem in second superblock
[ 8.975676] FAT-fs (sda1): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 8.977521] FAT-fs (sda1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.
[ 8.980907] FAT-fs (sda2): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 9.071104] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[ 9.075238] FAT-fs (sda3): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 9.107563] UDF-fs: warning (device sda3): udf_fill_super: No partition found (1)
[ 9.110274] F2FS-fs (sda3): Magic Mismatch, valid(0xf2f52010) - read(0x1)
[ 9.110285] F2FS-fs (sda3): Can't find a valid F2FS filesystem in first superblock
[ 9.110512] F2FS-fs (sda3): Magic Mismatch, valid(0xf2f52010) - read(0x4c3842)
[ 9.110522] F2FS-fs (sda3): Can't find a valid F2FS filesystem in second superblock
[ 9.112758] FAT-fs (sdc1): utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[ 14.132267] cloop: Can't open device read-write in mode 0x1f
[ 14.167382] cloop: losetup_file: 78484 blocks, 131072 bytes/block, largest block is 131098 bytes.
[ 14.191805] ISO 9660 Extensions: RRIP_1991A
[ 26.784147] [drm] radeon kernel modesetting enabled.
[ 27.081400] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[ 27.099673] snd_hda_intel 0000:00:01.1: enabling device (0000 -> 0002)
[ 27.100213] snd_hda_intel 0000:00:01.1: irq 77 for MSI/MSI-X
[ 27.122306] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[ 27.127491] r8169 0000:01:00.0: irq 78 for MSI/MSI-X
[ 27.128044] r8169 0000:01:00.0 eth0: RTL8168g/8111g at 0xffffc9000001a000, f8:0f:41:8e:0a:86, XID 0c000800 IRQ 78
[ 27.128057] r8169 0000:01:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[ 36.332221] Adding 2596364k swap on /dev/zram0. Priority:0 extents:1 across:2596364k SS
[ 37.474926] r8169 0000:01:00.0 eth0: unable to load firmware patch rtl_nic/rtl8168g-1.fw (-2)
[ 37.482552] r8169 0000:01:00.0 eth0: link down
[ 37.482583] r8169 0000:01:00.0 eth0: link down
[ 40.417115] r8169 0000:01:00.0 eth0: link up
[ 40.549497] NET: Registered protocol family 10
[ 46.283219] wmi: Mapper loaded
[ 46.664939] kvm: Nested Virtualization enabled
[ 46.664949] kvm: Nested Paging enabled
[ 56.446577] lp: driver loaded but no devices found
[ 56.491664] ppdev: user-space parallel port driver
[ 287.484680] aufs may_rename_srcdir:488:URL Classifier[3569]: renaming dir who has child(ren) on multiple branches, is not supported

---

### Post by AndyGaskell on 2013-11-18
hardinfo output on Knoppix (KNOPPIX_V7.2.0DVD-2013-06-16-EN)...

Computer
 
Summary
Computer
Processor       4x AMD A4-5000 APU with Radeon(TM) HD Graphics
Memory  3461MB (349MB used)
Operating System        Debian GNU/Linux 7.1
User Name       knoppix (Knoppix User)
Date/Time       Mo 18 Nov 2013 22:18:42 CET
Display
Resolution      1280x1024 pixels
OpenGL Renderer Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)
X11 Vendor      The X.Org Foundation
Multimedia
Audio Adapter   HDA-Intel - HD-Audio Generic
Audio Adapter   HDA-Intel - HD-Audio Generic
Input Devices
Power Button   
Power Button   
CHICONY USB Keyboard   
CHICONY USB Keyboard   
USB Optical Mouse      
Printers
No printers found      
SCSI Disks
ATA ST500DM002-1BD14   
HL-DT-ST DVDRAM GHA2N  
Multiple Card Reader   
Lexar USB Flash Drive  
Operating System
Version
Kernel  Linux 3.9.6-64 (x86_64)
Compiled        #23 SMP PREEMPT Sat Jun 15 14:15:39 CEST 2013
C Library       Unknown
Default C Compiler      GNU C Compiler version 4.7.2 (Debian 4.7.2-5)
Distribution    Debian GNU/Linux 7.1
Current Session
Computer Name   Microknoppix
User Name       knoppix (Knoppix User)
Home Directory  /home/knoppix
Desktop Environment     Unknown (Window Manager: Metacity)
Misc
Uptime  54 minutes
Load Average    0,00, 0,00, 0,00
Kernel Modules
Loaded Modules
parport_pc      PC-style parallel port driver
ppdev  
lp     
parport
kvm_amd
kvm    
crc32_pclmul   
ghash_clmulni_intel     GHASH Message Digest Algorithm, acclerated by PCLMULQDQ-NI
wmi     ACPI-WMI Mapping Driver
serio_raw       Raw serio driver
ipv6    IPv6 protocol stack for Linux
snd_hda_codec_realtek   Realtek HD-audio codec
snd_hda_codec_hdmi      HDMI HD-audio codec
r8169   RealTek RTL-8169 Gigabit Ethernet driver
snd_hda_intel   Intel HDA driver
mii     MII hardware support library
fam15h_power    AMD Family 15h CPU processor power monitor
snd_hda_codec   HDA codec core
i2c_piix4       PIIX4 SMBus driver
radeon  ATI Radeon
ttm     TTM memory manager subsystem (for DRM device)
drm_kms_helper  DRM KMS helper
Boots
Boots
Mon Nov 18 21:24        3.9.6-64|-
Languages
Available Languages
be_BY   Belarusian locale for Belarus
be_BY.cp1251    Belarusian locale for Belarus
be_BY.utf8      Belarusian locale for Belarus
bg_BG   Bulgarian locale for Bulgaria
bg_BG.cp1251    Bulgarian locale for Bulgaria
bg_BG.utf8      Bulgarian locale for Bulgaria
cs_CZ   Czech locale for the Czech Republic
cs_CZ.iso88592  Czech locale for the Czech Republic
cs_CZ.utf8      Czech locale for the Czech Republic
czech   Czech locale for the Czech Republic
da_DK   Danish locale for Denmark
da_DK.iso88591  Danish locale for Denmark
da_DK.utf8      Danish locale for Denmark
danish  Danish locale for Denmark
dansk   Danish locale for Denmark
de_AT@euro      German locale for Austria with Euro
de_AT.iso885915 German locale for Austria with Euro
de_AT.utf8      German locale for Austria
de_CH   German locale for Switzerland
de_CH.iso88591  German locale for Switzerland
de_CH.utf8      German locale for Switzerland
de_DE   German locale for Germany
de_DE@euro      German locale for Germany with Euro
de_DE.iso88591  German locale for Germany
de_DE.iso885915 German locale for Germany with Euro
de_DE.utf8      German locale for Germany
deutsch German locale for Germany
en_GB   English locale for Britain
en_GB.iso88591  English locale for Britain
en_GB.iso885915 English locale for Britain
en_GB.utf8      English locale for Britain
en_IE@euro      English locale for Ireland with Euro
en_IE.iso885915 English locale for Ireland with Euro
en_IE.utf8      English locale for Ireland
en_US   English locale for the USA
en_US.iso88591  English locale for the USA
en_US.iso885915 English locale for the USA
en_US.utf8      English locale for the USA
es_ES@euro      Spanish locale for Spain with Euro
es_ES.iso885915 Spanish locale for Spain with Euro
es_ES.utf8      Spanish locale for Spain
fi_FI@euro      Finnish locale for Finland with Euro
fi_FI.iso885915 Finnish locale for Finland with Euro
fi_FI.utf8      Finnish locale for Finland
fr_FR@euro      French locale for France with Euro
fr_FR.iso885915 French locale for France with Euro
fr_FR.utf8      French locale for France
german  German locale for Germany
hebrew  Hebrew locale for Israel
he_IL   Hebrew locale for Israel
he_IL.iso88598  Hebrew locale for Israel
he_IL.utf8      Hebrew locale for Israel
hi_IN   Hindi language locale for India
hi_IN.utf8      Hindi language locale for India
hu_HU   Hungarian locale for Hungary
hu_HU.iso88592  Hungarian locale for Hungary
hu_HU.utf8      Hungarian locale for Hungary
hungarian       Hungarian locale for Hungary
it_IT@euro      Italian locale for Italy with Euro
it_IT.iso885915 Italian locale for Italy with Euro
it_IT.utf8      Italian locale for Italy
ja_JP.utf8      Japanese language locale for Japan
nl_NL@euro      Dutch locale for the Netherlands with Euro
nl_NL.iso885915 Dutch locale for the Netherlands with Euro
nl_NL.utf8      Dutch locale for the Netherlands
pl_PL   Polish locale for Poland
pl_PL.iso88592  Polish locale for Poland
pl_PL.utf8      Polish locale for Poland
polish  Polish locale for Poland
ru_RU.koi8r     Russian locale for Russia
ru_RU.utf8      Russian locale for Russia
russian Russian locale for Russia
sk_SK   Slovak locale for Slovak
sk_SK.iso88592  Slovak locale for Slovak
sk_SK.utf8      Slovak locale for Slovak
slovak  Slovak locale for Slovak
slovene Slovenian locale for Slovenia
slovenian       Slovenian locale for Slovenia
sl_SI   Slovenian locale for Slovenia
sl_SI.iso88592  Slovenian locale for Slovenia
sl_SI.utf8      Slovenian locale for Slovenia
tr_TR   Turkish locale for Turkey
tr_TR.iso88599  Turkish locale for Turkey
tr_TR.utf8      Turkish locale for Turkey
turkish Turkish locale for Turkey
zh_CN.utf8      Chinese locale for Peoples Republic of China
zh_TW.utf8      Chinese locale for Taiwan R.O.C.
Filesystems
Mounted File Systems
/dev/sdc1       /mnt-system     52,37 % (3,5 GiB of 7,3 GiB)
tmpfs   /ramdisk        0,84 % (2,6 GiB of 2,6 GiB)
/dev/cloop      /KNOPPIX        100,00 % (0,0 B of 9,6 GiB)
unionfs /UNIONFS        0,84 % (2,6 GiB of 2,6 GiB)
unionfs /usr    0,84 % (2,6 GiB of 2,6 GiB)
unionfs /home   0,84 % (2,6 GiB of 2,6 GiB)
tmpfs   /run    13,61 % (17,3 MiB of 20,0 MiB)
tmpfs   /UNIONFS/var/run        13,61 % (17,3 MiB of 20,0 MiB)
tmpfs   /UNIONFS/var/lock       0,00 % (10,0 MiB of 10,0 MiB)
tmpfs   /UNIONFS/var/log        0,05 % (99,9 MiB of 100,0 MiB)
tmpfs   /tmp    0,00 % (2,0 GiB of 2,0 GiB)
udev    /dev    0,02 % (20,0 MiB of 20,0 MiB)
tmpfs   /dev/shm        0,00 % (2,0 GiB of 2,0 GiB)
Display
Display
Resolution      1280x1024 pixels
Vendor  The X.Org Foundation
Version 1.12.4
Monitors
Monitor 0       1280x1024 pixels
Extensions
BIG-REQUESTS   
DAMAGE 
DOUBLE-BUFFER  
DPMS   
DRI2   
GLX    
Generic Event Extension
MIT-SCREEN-SAVER       
MIT-SHM
RANDR  
RECORD 
RENDER 
SECURITY       
SGI-GLX
SHAPE  
SYNC   
X-Resource     
XC-MISC
XFIXES 
XFree86-DGA    
XFree86-VidModeExtension       
XINERAMA       
XInputExtension
XKEYBOARD      
XTEST  
XVideo 
OpenGL
Vendor  VMware, Inc.
Renderer        Gallium 0.4 on llvmpipe (LLVM 3.2, 128 bits)
Version 2.1 Mesa 9.1.3
Direct Rendering        Yes
Environment Variables
Environment Variables
SSH_AGENT_PID   3294
SAL_USE_VCLPLUGIN       gtk
SPEECHD_ADDRESS unix_socket:/var/run/speech-dispatcher/speechd.sock
TERM    xterm
SHELL   /bin/bash
XDG_MENU_PREFIX lxde-
XDG_SESSION_COOKIE      7f2fcb52ce34afe36e290df148665669-1384806329.288234-737647862
LC_ALL  de_DE.UTF-8
USER    knoppix
QT_ACCESSIBILITY        1
SSH_AUTH_SOCK   /tmp/ssh-0ol64t4C85rH/agent.3184
PATH    /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
MAIL    /var/mail/knoppix
DESKTOP_SESSION LXDE
COUNTRY DE
LC_MESSAGES     de_DE.UTF-8
PWD     /home/knoppix
LANG    de_DE.UTF-8.UTF-8
HISTCONTROL     ignoreboth
_LXSESSION_PID  3299
HOME    /home/knoppix
SHLVL   2
XDG_CONFIG_HOME /home/knoppix/.config
LANGUAGE        de
GNOME_DESKTOP_SESSION_ID        LXDE
G_FILENAME_ENCODING     @locale
LOGNAME knoppix
XDG_DATA_DIRS   /usr/local/share/:/usr/share/:/usr/share/gdm/:/var/lib/menu-xdg/
DBUS_SESSION_BUS_ADDRESS        unix:abstract=/tmp/dbus-3PfM6EdVaa,guid=031dd16c7ccd81a3b70dd8ae528a77b9
WINDOWPATH      5
DISPLAY :0
STARTUP /usr/bin/ssh-agent /usr/bin/ck-launch-session /usr/bin/dbus-launch --exit-with-session startlxde
XDG_CURRENT_DESKTOP     LXDE
XAUTHORITY      /home/knoppix/.Xauthority
_       /usr/bin/hardinfo
Users
Users
root    root
daemon  daemon
bin     bin
sys     sys
sync    sync
games   games
man     man
lp      lp
mail    mail
news    news
uucp    uucp
proxy   proxy
www-data        www-data
backup  backup
list    Mailing List Manager
irc     ircd
gnats   Gnats Bug-Reporting System (admin)
nobody  nobody
libuuid
messagebus     
knoppix Knoppix User
haldaemon       Hardware abstraction layer
speech-dispatcher       Speech Dispatcher
polkituser      PolicyKit
festival       
saned  
statd  
partimag        Partimage Server
sshd   
tftp    tftp daemon
hplip   HPLIP system user
avahi   Avahi mDNS daemon
bacula  Bacula
mysql   MySQL Server
snort   Snort IDS
bind   
clamav 
freerad
postgres        PostgreSQL administrator
privoxy
debian-tor     
vde2-net       
timidity        TiMidity++ MIDI sequencer service
usbmux  usbmux daemon
ntop   
kdm    
libvirt-qemu    Libvirt Qemu
colord  colord colour management daemon
nx     
dirmngr
syslog 
klog   
debian-spamd   
distccd
xrdp   
Devices
 
Processor
Processors
AMD A4-5000 APU with Radeon(TM) HD Graphics     1500,00MHz
AMD A4-5000 APU with Radeon(TM) HD Graphics     1500,00MHz
AMD A4-5000 APU with Radeon(TM) HD Graphics     800,00MHz
AMD A4-5000 APU with Radeon(TM) HD Graphics     1500,00MHz
Memory
Memory
Total Memory    3461824 kB
Free Memory     2538832 kB
Buffers 16108 kB
Cached  573848 kB
Cached Swap     0 kB
Active  356304 kB
Inactive        469768 kB
Active(anon)    245368 kB
Inactive(anon)  19280 kB
Active(file)    110936 kB
Inactive(file)  450488 kB
Unevictable     0 kB
Mlocked 0 kB
Virtual Memory  2596364 kB
Free Virtual Memory     2596364 kB
Dirty   0 kB
Writeback       0 kB
AnonPages       236220 kB
Mapped  60796 kB
Shmem   28480 kB
Slab    69424 kB
SReclaimable    40300 kB
SUnreclaim      29124 kB
KernelStack     2096 kB
PageTables      4624 kB
NFS_Unstable    0 kB
Bounce  0 kB
WritebackTmp    0 kB
CommitLimit     4327276 kB
Committed_AS    1037840 kB
VmallocTotal    34359738367 kB
VmallocUsed     297232 kB
VmallocChunk    34359436496 kB
HardwareCorrupted       0 kB
HugePages_Total 0
HugePages_Free  0
HugePages_Rsvd  0
HugePages_Surp  0
Hugepagesize    2048 kB
DirectMap4k     21148 kB
DirectMap2M     2555904 kB
DirectMap1G     1048576 kB
PCI Devices
PCI Devices
Host bridge     Advanced Micro Devices [AMD] Family 16h Processor Root Complex
VGA compatible controller       Advanced Micro Devices [AMD] nee ATI Device 9832
Audio device    Advanced Micro Devices [AMD] nee ATI Device 9840
Host bridge     Advanced Micro Devices [AMD] Family 16h Processor Function 0
PCI bridge      Advanced Micro Devices [AMD] Family 16h Processor Functions 5:1
USB controller  Advanced Micro Devices [AMD] FCH USB XHCI Controller
SATA controller Advanced Micro Devices [AMD] FCH SATA Controller [IDE mode]
USB controller  Advanced Micro Devices [AMD] FCH USB OHCI Controller
USB controller  Advanced Micro Devices [AMD] FCH USB EHCI Controller
USB controller  Advanced Micro Devices [AMD] FCH USB OHCI Controller
USB controller  Advanced Micro Devices [AMD] FCH USB EHCI Controller
SMBus   Advanced Micro Devices [AMD] FCH SMBus Controller
Audio device    Advanced Micro Devices [AMD] FCH Azalia Controller
ISA bridge      Advanced Micro Devices [AMD] FCH LPC Bridge
Host bridge     Advanced Micro Devices [AMD] Family 16h Processor Function 0
Host bridge     Advanced Micro Devices [AMD] Family 16h Processor Function 1
Host bridge     Advanced Micro Devices [AMD] Family 16h Processor Function 2
Host bridge     Advanced Micro Devices [AMD] Family 16h Processor Function 3
Host bridge     Advanced Micro Devices [AMD] Family 16h Processor Function 4
Host bridge     Advanced Micro Devices [AMD] Family 16h Processor Function 5
Ethernet controller     Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
USB Devices
Printers
Printers
No printers found      
Battery
No batteries
No batteries found on this system      
Sensors
Cooling Fans
Temperatures
Voltage Values
Input Devices
Input Devices
Power Button   
Power Button   
CHICONY USB Keyboard   
CHICONY USB Keyboard   
USB Optical Mouse      
Storage
SCSI Disks
ATA ST500DM002-1BD14   
HL-DT-ST DVDRAM GHA2N  
Multiple Card Reader   
Lexar USB Flash Drive  
DMI
BIOS
Date    04/26/2013
Vendor  American Megatrends Inc. ([www.ami.com](www.ami.com))
Version P11-A1L
Board
Name    Aspire XC-105
Vendor  Acer ([www.acer.com](www.acer.com))
Resources
I/O Ports
0000-03af       PCI Bus 0000:00
0000-001f       dma1
0020-0021       pic1
0040-0043       timer0
0050-0053       timer1
0060-0060       keyboard
0064-0064       keyboard
0070-0071       rtc0
0080-008f       dma page reg
00a0-00a1       pic2
00c0-00df       dma2
00f0-00ff       fpu
0170-0177       pata_legacy
01f0-01f7       pata_legacy
0376-0376       pata_legacy
03b0-03df       PCI Bus 0000:00
03e0-0cf7       PCI Bus 0000:00
03f6-03f6       pata_legacy
040b-040b       pnp 00:02
04d0-04d1       pnp 00:02
04d0-04d1       pnp 00:08
04d6-04d6       pnp 00:02
0800-089f       pnp 00:02
0800-0803       ACPI PM1a_EVT_BLK
0804-0805       ACPI PM1a_CNT_BLK
0808-080b       ACPI PM_TMR
0810-0815       ACPI CPU throttle
0820-0827       ACPI GPE0_BLK
0900-090f       pnp 00:02
0910-091f       pnp 00:02
0a00-0a1f       pnp 00:03
0a20-0a2f       pnp 00:03
0a30-0a3f       pnp 00:03
0b00-0b07       piix4_smbus
0b20-0b3f       pnp 00:02
0c00-0c01       pnp 00:02
0c14-0c14       pnp 00:02
0c50-0c51       pnp 00:02
0c52-0c52       pnp 00:02
0c6c-0c6c       pnp 00:02
0c6f-0c6f       pnp 00:02
0cd0-0cd1       pnp 00:02
0cd2-0cd3       pnp 00:02
0cd4-0cd5       pnp 00:02
0cd6-0cd7       pnp 00:02
0cd8-0cdf       pnp 00:02
0cf8-0cff       PCI conf1
0d00-ffff       PCI Bus 0000:00
e000-efff       PCI Bus 0000:01
e000-e0ff       Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
e000-e0ff       RealTek RTL-8169 Gigabit Ethernet driver
f000-f0ff       Advanced Micro Devices [AMD] nee ATI Device 9832
f100-f10f       Advanced Micro Devices [AMD] FCH SATA Controller [IDE mode]
f100-f10f       ahci
f110-f113       Advanced Micro Devices [AMD] FCH SATA Controller [IDE mode]
f110-f113       ahci
f120-f127       Advanced Micro Devices [AMD] FCH SATA Controller [IDE mode]
f120-f127       ahci
f130-f133       Advanced Micro Devices [AMD] FCH SATA Controller [IDE mode]
f130-f133       ahci
f140-f147       Advanced Micro Devices [AMD] FCH SATA Controller [IDE mode]
f140-f147       ahci
fe00-fefe       pnp 00:02
Memory
00000000-00000fff       reserved
00001000-0009ffff       System RAM
000a0000-000bffff       PCI Bus 0000:00
000c0000-000dffff       PCI Bus 0000:00
000f0000-000fffff       System ROM
00100000-9c821fff       System RAM
02000000-02735b39       Kernel code
02735b3a-02ccf9ff       Kernel data
02db7000-02e50fff       Kernel bss
9c822000-9c9a3fff       reserved
9c9a4000-9c9c8fff       ACPI Tables
9c9c9000-9d371fff       ACPI Non-volatile Storage
9d372000-9e5a4fff       reserved
9e5a5000-9e5a5fff       System RAM
9e5a6000-9e5adfff       ACPI Non-volatile Storage
9e5ae000-9e706fff       System RAM
9e707000-9ec2efff       reserved
9ec2f000-9ec6ffff       System RAM
9ec70000-9eff0fff       reserved
9eff1000-9effffff       System RAM
9f000000-9fffffff       RAM buffer
a0000000-bfffffff       pnp 00:01
c0000000-ffffffff       PCI Bus 0000:00
c0000000-cfffffff       Advanced Micro Devices [AMD] nee ATI Device 9832
c0000000-c04fffff       efifb
d0000000-d07fffff       Advanced Micro Devices [AMD] nee ATI Device 9832
d0800000-d08fffff       PCI Bus 0000:01
d0800000-d0803fff       Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
d0800000-d0803fff       RealTek RTL-8169 Gigabit Ethernet driver
d0804000-d0804fff       Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller
d0804000-d0804fff       RealTek RTL-8169 Gigabit Ethernet driver
e0000000-efffffff       PCI MMCONFIG 0000 [bus 00-ff]
e0000000-efffffff       pnp 00:00
fec00000-fec01fff       reserved
fec00000-fec003ff       IOAPIC 0
fec01000-fec013ff       IOAPIC 1
fec10000-fec10fff       reserved
fec10000-fec10fff       pnp 00:02
fed00000-fed00fff       reserved
fed00000-fed00fff       pnp 00:02
fed00000-fed003ff       HPET 0
fed61000-fed70fff       pnp 00:02
fed80000-fed8ffff       reserved
fed80000-fed8ffff       pnp 00:02
fee00000-fee00fff       Local APIC
fee00000-fee00fff       pnp 00:02
fef00000-fef3ffff       Advanced Micro Devices [AMD] nee ATI Device 9832
fef40000-fef5ffff       Advanced Micro Devices [AMD] nee ATI Device 9832
fef60000-fef63fff       Advanced Micro Devices [AMD] FCH Azalia Controller
fef60000-fef63fff       ICH HD audio
fef64000-fef67fff       Advanced Micro Devices [AMD] nee ATI Device 9840
fef64000-fef67fff       ICH HD audio
fef68000-fef69fff       Advanced Micro Devices [AMD] FCH USB XHCI Controller
fef68000-fef69fff       xhci_hcd
fef6a000-fef6a0ff       Advanced Micro Devices [AMD] FCH USB EHCI Controller
fef6a000-fef6a0ff       ehci_hcd
fef6b000-fef6bfff       Advanced Micro Devices [AMD] FCH USB OHCI Controller
fef6b000-fef6bfff       ohci_hcd
fef6c000-fef6c0ff       Advanced Micro Devices [AMD] FCH USB EHCI Controller
fef6c000-fef6c0ff       ehci_hcd
fef6d000-fef6dfff       Advanced Micro Devices [AMD] FCH USB OHCI Controller
fef6d000-fef6dfff       ohci_hcd
fef6e000-fef6e3ff       Advanced Micro Devices [AMD] FCH SATA Controller [IDE mode]
fef6e000-fef6e3ff       ahci
ff000000-ffffffff       reserved
ff000000-ffffffff       pnp 00:02
100001000-13effffff     System RAM
13f000000-13fffffff     RAM buffer
DMA
4       cascade
Network
 
Interfaces
Network Interfaces
eth0    3,71MiB 0,28MiB 192.168.1.86
lo      0,00MiB 0,00MiB 127.0.0.1
IP Connections
Connections
127.0.0.1:631   LISTEN  0.0.0.0:*       tcp
::1:631 LISTEN  :::*    tcp6
0.0.0.0:34211           0.0.0.0:*       udp
0.0.0.0:68              0.0.0.0:*       udp
0.0.0.0:631             0.0.0.0:*       udp
:::35058                :::*    udp6
Routing Table
IP routing table
0.0.0.0 / 192.168.1.254 0.0.0.0 UG      eth0
192.168.1.0 / 0.0.0.0   255.255.255.0   U       eth0
ARP Table
ARP Table
192.168.1.254   00:1f:9f:11:a7:1a       eth0
192.168.1.84    00:21:5a:21:5a:81       eth0
DNS Servers
Name servers
192.168.1.254  
Statistics
IP
3173    Total packets received
0       Incoming packets discarded
0       Incoming packets discarded
3153    Incoming packets delivered
2392    Requests sent out
ICMP
0       ICMP messages failed
0       ICMP messages failed
162     ICMP messages sent
0       ICMP messages failed
ICMPMSG
TCP
44      Active connections openings
0       Bad segments received.
8       Failed connection attempts
0       Bad segments received.
0       Bad segments received.
2832    Segments received
2167    Segments send out
0       Bad segments received.
0       Bad segments received.
9       Resets sent
UDP
69      Packets sent
162     Packets to unknown port received.
0       Packet receive errors
69      Packets sent
UDPLITE
TCPEXT
10      TCP sockets finished time wait in fast timer
22      Delayed acks sent
1       Delayed acks further delayed because of locked socket
2063    Packet headers predicted
80      Acknowledgments not containing data payload received
115     Predicted acknowledgments
4       DSACKs sent for old packets
IPEXT
Shared Directories
SAMBA
NFS
Benchmarks
 
CPU Blowfish
CPU Blowfish
This Machine    1500 MHz        5,209
Intel(R) Celeron(R) M processor 1.50GHz (null)  26.1876862
PowerPC 740/750 (280.00MHz)     (null)  172.816713
CPU CryptoHash
CPU CryptoHash
This Machine    1500 MHz        229,051
CPU Fibonacci
CPU Fibonacci
This Machine    1500 MHz        5,181
Intel(R) Celeron(R) M processor 1.50GHz (null)  8.1375674
PowerPC 740/750 (280.00MHz)     (null)  58.07682
CPU N-Queens
CPU N-Queens
This Machine    1500 MHz        11,156
FPU FFT
FPU FFT
This Machine    1500 MHz        3,030
FPU Raytracing
FPU Raytracing
This Machine    1500 MHz        16,675
Intel(R) Celeron(R) M processor 1.50GHz (null)  40.8816714
PowerPC 740/750 (280.00MHz)     (null)  161.312647

---

### Post by TDave on 2013-11-18
Bit more from me then.

So, when I boot up, I don't get to the Login Manager, but I do get a graphical interface with a warning box in the centre telling me:
> **The system is running in low-graphics mode**
Your screen, graphics card, and input device settings could not be detected correctly. You will need to configure these yourself.

I was incorrect in what I described earlier - clicking "OK" at this point takes me to a multiple choice window:
> What would you like to do?
- Run in low-graphics mode for just one session
- Reconfigure graphics
- Troubleshoot the error
- Exit to console login

- Choosing "Low-Graphics" prompts me to wait one minute while the display restarts. When nothing, clicking OK on that dumps me to the console login
- Choosing "Reconfigure Graphics" gets me into a window loop, asking whether I want to "Use the Default Config" or the "Backed-Up Config" - I get the impression this is to help those with driver upgrade trouble
- Choosing "Troubleshoot" doesn't give me much, other than a printout of Xorg.0.log (attached). Looking at that, it seems the card isn't supported by the default installed X drivers. The startup errors page is blank. I didn't bother editing the config file yet. Xorg.conf is on it's failsafe mode at the minute, which is struggling...
- Choosing "Exit to Console Login"... well, I'll let you guess that.

From the key components of the original error (Dsplay, Input, and Graphics) points the finger firmly at X (it's not Mir yet, right?).

Here's my Ubuntu lspci:
```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Root Complex
00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8330]
00:01.1 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] Device 9840
00:02.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:02.5 PCI bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Functions 5:1 
00:10.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB XHCI Controller (rev 01) 
00:11.0 SATA controller: Advanced Micro Devices, Inc. [AMD] FCH SATA Controller [AHCI mode] (rev 40) 
00:12.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39) 
00:12.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39) 
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB OHCI Controller (rev 39) 
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD] FCH USB EHCI Controller (rev 39)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD] FCH SMBus Controller (rev 3a)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD] FCH Azalia Controller (rev 02)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD] FCH LPC Bridge (rev 11)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 0
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 1
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 2
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 3
00:18.4 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 4
00:18.5 Host bridge: Advanced Micro Devices, Inc. [AMD] Family 16h Processor Function 5
01:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)

```

Given the error, the important bit should be **VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Kabini [Radeon HD 8330]**

Now, I've got a bunch of Radeon / AMD stuff installed for X already, which I thought would at least get me something viewable, but apparently not. :)
A quick Google search doesn't give much hope on that Kabini HD 8330 front, but I figured I had nothing to lose by going the proprietary route - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI) - yes, I'd rather use open drivers (and there are many good reasons not to touch fglrx with a bargepole) but I'd also rather use Ubuntu for this particular PC than anything else, particularly Windaz, which is my only other option at the minute, from an acceptability perspective that is.

---

### Post by TDave on 2013-11-18
Edit is failing me. Here's the pastebin of the Xorg.0.log - [http://paste.ubuntu.com/6439905/](http://paste.ubuntu.com/6439905/)

Currently installing fglrx, so we'll see if that yields any results. Looking at the big list of cards in the log output above, it looks to me like the Graphics part of the chip isn't supported by the open source drivers yet.

---

### Post by TDave on 2013-11-18
So far, so good. 

**apt-get install fglrx** followed by a reboot has resulted in a bootable environment.

I can't pretend to have done much more than that, nor have I put it through it's paces, but it's booted at a reasonable resolution (only on VGA atm) and Catalyst Control Centre seems to have picked everything up.

I'll endeavour to play with it more tomorrow.

---

### Post by AndyGaskell on 2013-11-18
Hi TDave

I'd like to say "bingo", but got a bit more testing to do to be sure. From your...
>  I might also check this by trying to live-boot something Arch-based or similarly "bleeding edge"
...I thought I'd try a newer version of Ubuntu, so I downloaded...
[http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/trusty-desktop-amd64.iso) (18-Nov-2013 07:44  895M  Desktop image for 64-bit PC (AMD64) computers (standard download)  )
...from...
[URL="http://cdimage.ubuntu.com/daily-live/current/"]http://cdimage.ubuntu.com/daily-live/current/
[/URL]...and it seems to work ok.  I've only just got it installed (ran it as tryout, then installed from there) so have more testing to do, but so-far-so-good.  If this works out, then it looks like we're good for future releases of Ubuntu, if not for the current one just now.

Will update after more testing tomorrow.

:D

---

### Post by AndyGaskell on 2013-11-18
Seems to be all good, done some more testing, tried both with video on VGA/DSUB and HDMI/DVI and all ok.

It boots up pretty quick too, so much so that I actually timed it, from cold push of the power button to booted up was 35 seconds, nice :)

---

### Post by TDave on 2013-11-19
Happy days. Trying a daily / nightly was something I was toying with, but as I didn't want to leave it running that until the full release in April I decided against it. Given I got a desktop environment using fglrx, I'm probably not even going to try anything else in the short term.

System was running fine last night, the only thing I noticed that I hadn't spotted earlier was that somehow I must have downloaded the 32-bit Mini ISO, as that's what was installed. Downloaded a fresh copy of it (definitely 64-bit this time!) and will reinstall with that again. Hopefully the mistake was just mine.

Good to hear we're getting somewhere though!

---

### Post by AndyGaskell on 2013-11-19
Yea, the daily install does seem a little flaky, as you'd expect really, just things like app center crashing and vino vnc server not starting up.  So I think Ubuntu 13.10 with fglrx might be a better option until April.  I'll run with the daily for a day or two and try and get a better feeling of how stable it is, if I can't sort out these wee niggles, I'll switch to the 13.10 with fglrx option.

---

### Post by TDave on 2013-11-20
Realized I was missing a beat with the mini.iso, so for my reinstall I simply used the server amd64 ISO to give me a booting command line system (using EFI) and then **apt-get install ubuntu-desktop fglrx** to get something that boots up.

I'm fairly sure I'll end up missing some odd libraries this way, but I've got a working system now with a graphical interface, that'll at least tie me over until 14.04.

---

### Post by AndyGaskell on 2013-11-23
Hi TD

I've decided to ditch the trusty-desktop-amd64 daily as it was too crash prone, seemed to lock up every couple of days.  So, I though I'd try your route.

So, I've been trying the ubuntu-13.10-server-amd64.iso, as per you last post, and it just hangs on the first screen of installation, the language selection.  I've tried with EFI on and off, with no luck.  Any pointers on what you did to get it to work?  Is this the same ISO?  Did you do anything in particular during install?

I'll keep experimenting here, but any tips would be cool, thanks.

---

### Post by TDave on 2013-11-27
Hi Andy,

Afraid I didn't do anything particularly special on my install, although as you pointed out I did leave UEFI on (I can't remember the specific option, but there's one option in the Acer setup utility that automatically detects UEFI / Legacy on boot media - I left that enabled) and chose the EFI boot option from the CD.

To cover the key points:
 - Acer setup stuff was configured to do the automatic detection of UEFI / Legacy. SecureBoot was off, obviously
 - I used ubuntu-13.10-server-amd64.iso as the install medium. I specifically wrote it to CD, rather than creating a USB boot key.
 - Got the UEFI boot menu on the CD. Selected the default "Install Server" option to get to the CLI installer.
 - Ran through the installer and partitioning without issue. Not that it affects your current scenario, but I did the partitions manually for my own LVM requirements / preferences
 - Rebooted to the command prompt, apt-get installed ubuntu-desktop, fglrx and anything else I wanted.
 - Reboot again and, voila!

For the mini.iso, the steps were largely the same except I didn't bother with LVM, and there was no UEFI boot. As I was just testing with the mini.iso at that point I pretty much blitzed through the installer, just to see what worked.

It's weird that both are hanging at the language selection, which is after the thing's booted. Seems unlikely, but have you checked the disk integrity / checksummed the image?

---

### Post by AndyGaskell on 2013-12-03
Hi TD

Thanks for the reply, much appreciated. I didn't get a chance to look at it last week, been a bit snowed under.  You're notes are really handy, gives me some thoughts on the cause of my issues and what to try next. 

So, the main difference I guess is that I'm using USB rather than CD, perhaps there are bugs in the USB support for the motherboard somewhere in the installer.  I had checked the media, both server and ISO, and it did come up with some errors.  Seeing this I checked my ISO files (with the torrent checksum) and they were ok.  I also putting the ISO onto the usb stick on Windows 7 desktop and my Ubuntu 13.10 laptop.  Tried 2 different USB sticks too, one brand new one.  After doing all this I kind of put the disk check errors down to being false negatives.  Looking back, and with you're notes too, I guess there is a USB issue there.  The daft thing is, I'm not sure I have a CD or DVD burner anywhere, except in the XC-105.  Definitely sounds like installing from CD/DVD is a good plan.

I was thinking the issues might also be caused by me trying to install over 14.04 Trusty daily, so might also try formatting the HD before installing.

I noticed these Acer Aspire XC-105 were now £10 off in eBuyer now.

Hopefully I'll get more time to tinker with it this weekend.  Will post any progress.

---

### Post by open2reason on 2014-02-08
Andy, 
Having the same spec kit as you I also failed on 13.10 but 12.04lts is working with latest fglrx driver.
14.04 may be better [http://ubuntuforums.org/showthread.php?t=2204325&p=12923286#post12923286](http://ubuntuforums.org/showthread.php?t=2204325&p=12923286#post12923286)

ATB

---

### Post by AndyGaskell on 2014-02-12
Hi open2reason

Thanks for the post, good info to have, and a handy x-ref.  Was your system a Acer Aspire XC-105, or a different system with similar hardware?

From looking at it all, me and TDave here found 2 options...

Ubuntu 13.10 (Saucy Salamander) with fglrx 

...or...

Ubuntu 14.04 (Trusty Tahr), pre release Daily Build, full release due April 2014

---

### Post by open2reason on 2014-02-12
Andy,
My kit is an Acer Aspire XC-105 Desktop AMD A4-5000 1.5GHz, 4GB RAM, 500GB HDD, DVD, LAN, Integrated Graphics created in September 2013 and purchased as a second box while my laptop was being repaired.
I almost cried upon seeing the graphics under 12.04.4 prior to installing the fglrx drivers but now feel somewhat better after trying the open source drivers under 14.04 lts daily build.
Can't wait for 14.04 lts.  [http://ubuntuforums.org/showthread.php?t=2204560](http://ubuntuforums.org/showthread.php?t=2204560)

Thanks a lot for the info and advice you have provided.

ps the deal included a 23" screen [http://ubuntuforums.org/attachment.php?attachmentid=250203&d=1391949516](http://ubuntuforums.org/attachment.php?attachmentid=250203&d=1391949516) and that helped me see the value of this simple system as a second box.

---

### Post by open2reason on 2014-02-14
Andy and TDave,
I happened to notice the Crucial are advertising SSD & RAM that is compatible [http://www.crucial.com/uk/store/listparts.aspx?mfr=Acer&model=Aspire%20XC105](http://www.crucial.com/uk/store/listparts.aspx?mfr=Acer&model=Aspire%20XC105) with our xc-105s, so, are either of you considering these upgrade? ;)
I myself am awaiting 14.04 to see what speed ups may accrue to my box.
I know I may not need it but thoughts keep returning to more RAM. . .

Am happy with kit and awaiting 14.04lts.

---

### Post by AndyGaskell on 2014-05-14
Just a quick update on this, the XC-105 is now running sweetly on 14.04 stable as you would expect, and with no fglx.

Shame that now they are harder to find, at least at the the low price they were on for initially.

---

