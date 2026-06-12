---
title: "Samsung YP-U3 ZW Help!"
date: 2007-09-01
forum: Hardware &amp; Laptops
---

### Post by badmotor on 2007-09-01
My wife just bought me one of these for fathers day, I plugged it straight into my PC with 7.04 on it, and it doesn't even recognise the device!
First time my my computer hasn't recognised something ( Started using Ubuntu a month or so ago ). I like the mp3 player, and my wife is eyeing Ubuntu suspiciously, like it is to blame, and I'm thinking "I'm sure there is a fix for this somewhere"...

Can anyone shed some light? Thanks guys.:guitar:

---

### Post by CRCarl on 2007-09-02
Can you send us some info please - 

With the device unplugged, run ```
lsusb
```. Then plug the device in and run ```
 lsusb 
```again.

Then run ```
 tail -n 100 /var/log/messages
```

Copy and paste all of the output up here.

Thanks, 

C

---

### Post by badmotor on 2007-09-03
Alright Carl, here are the results:   (What do they tell you?)

todd@todd-desktop:~$ lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05a9:8519 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 0000:0000  
todd@todd-desktop:~$ lsusb
Bus 004 Device 004: ID 04e8:507d Samsung Electronics Co., Ltd 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 046d:c00c Logitech, Inc. Optical Wheel Mouse
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 003: ID 05a9:8519 OmniVision Technologies, Inc. 
Bus 001 Device 001: ID 0000:0000  
todd@todd-desktop:~$ tail -n 100 /var/log/messages
Sep  3 19:54:31 todd-desktop kernel: [   24.804978] ata2: PATA max UDMA/100 cmd 0x00010170 ctl 0x00010376 bmdma 0x00011868 irq 15
Sep  3 19:54:31 todd-desktop kernel: [   24.805008] scsi0 : ata_piix
Sep  3 19:54:31 todd-desktop kernel: [   24.818447] 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
Sep  3 19:54:31 todd-desktop kernel: [   24.898844] Floppy drive(s): fd0 is 1.44M
Sep  3 19:54:31 todd-desktop kernel: [   24.919132] FDC 0 is a post-1991 82077
Sep  3 19:54:31 todd-desktop kernel: [   24.972496] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Sep  3 19:54:31 todd-desktop kernel: [   24.972503] ata1.00: ATA-5: WDC WD400EB-11CPF0, 06.04G06, max UDMA/100
Sep  3 19:54:31 todd-desktop kernel: [   24.972507] ata1.00: 78165360 sectors, multi 16: LBA 
Sep  3 19:54:31 todd-desktop kernel: [   24.984463] ata1.00: ata_hpa_resize 1: sectors = 78165360, hpa_sectors = 78165360
Sep  3 19:54:31 todd-desktop kernel: [   24.984469] ata1.00: configured for UDMA/100
Sep  3 19:54:31 todd-desktop kernel: [   24.984489] scsi1 : ata_piix
Sep  3 19:54:31 todd-desktop kernel: [   25.307285] ata2.00: ATAPI, max UDMA/33
Sep  3 19:54:31 todd-desktop kernel: [   25.418757] usb 1-1: new full speed USB device using uhci_hcd and address 3
Sep  3 19:54:31 todd-desktop kernel: [   25.475045] ata2.00: configured for UDMA/33
Sep  3 19:54:31 todd-desktop kernel: [   25.475264] scsi 0:0:0:0: Direct-Access     ATA      WDC WD400EB-11CP 06.0 PQ: 0 ANSI: 5
Sep  3 19:54:31 todd-desktop kernel: [   25.477581] scsi 1:0:0:0: CD-ROM            COMBI    RW16x10/DVD      H1.0 PQ: 0 ANSI: 5
Sep  3 19:54:31 todd-desktop kernel: [   25.615540] usb 1-1: configuration #1 chosen from 1 choice
Sep  3 19:54:31 todd-desktop kernel: [   25.858190] usb 2-1: new low speed USB device using uhci_hcd and address 2
Sep  3 19:54:31 todd-desktop kernel: [   25.979006] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Sep  3 19:54:31 todd-desktop kernel: [   25.980219] sda: Write Protect is off
Sep  3 19:54:31 todd-desktop kernel: [   25.982177] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  3 19:54:31 todd-desktop kernel: [   25.983167] SCSI device sda: 78165360 512-byte hdwr sectors (40021 MB)
Sep  3 19:54:31 todd-desktop kernel: [   25.986028] sda: Write Protect is off
Sep  3 19:54:31 todd-desktop kernel: [   25.990012] SCSI device sda: write cache: enabled, read cache: enabled, doesn't support DPO or FUA
Sep  3 19:54:31 todd-desktop kernel: [   25.990021]  sda: sda1 sda2 <<6>usb 2-1: configuration #1 chosen from 1 choice
Sep  3 19:54:31 todd-desktop kernel: [   26.056603]  sda5 >
Sep  3 19:54:31 todd-desktop kernel: [   26.056777] sd 0:0:0:0: Attached scsi disk sda
Sep  3 19:54:31 todd-desktop kernel: [   26.064584] sd 0:0:0:0: Attached scsi generic sg0 type 0
Sep  3 19:54:31 todd-desktop kernel: [   26.064619] sr 1:0:0:0: Attached scsi generic sg1 type 5
Sep  3 19:54:31 todd-desktop kernel: [   26.073617] sr0: scsi3-mmc drive: 40x/40x writer cd/rw xa/form2 cdda tray
Sep  3 19:54:31 todd-desktop kernel: [   26.073625] Uniform CD-ROM driver Revision: 3.20
Sep  3 19:54:31 todd-desktop kernel: [   26.475707] usbcore: registered new interface driver hiddev
Sep  3 19:54:31 todd-desktop kernel: [   26.508391] input: Logitech USB Optical Mouse as /class/input/input2
Sep  3 19:54:31 todd-desktop kernel: [   26.508432] input: USB HID v1.10 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1d.1-1
Sep  3 19:54:31 todd-desktop kernel: [   26.508459] usbcore: registered new interface driver usbhid
Sep  3 19:54:31 todd-desktop kernel: [   26.508464] drivers/usb/input/hid-core.c: v2.6:USB HID core driver
Sep  3 19:54:31 todd-desktop kernel: [   27.911653] Attempting manual resume
Sep  3 19:54:31 todd-desktop kernel: [   28.538776] kjournald starting.  Commit interval 5 seconds
Sep  3 19:54:31 todd-desktop kernel: [   28.538804] EXT3-fs: mounted filesystem with ordered data mode.
Sep  3 19:54:31 todd-desktop kernel: [   52.313539] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1
Sep  3 19:54:31 todd-desktop kernel: [   53.840437] NET: Registered protocol family 17
Sep  3 19:54:31 todd-desktop kernel: [   54.833368] i810_smbus 0000:00:02.0: i810/i815 i2c device found.
Sep  3 19:54:31 todd-desktop kernel: [   55.085609] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
Sep  3 19:54:31 todd-desktop kernel: [   55.088795] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
Sep  3 19:54:31 todd-desktop kernel: [   55.132800] iTCO_vendor_support: vendor-support=0
Sep  3 19:54:31 todd-desktop kernel: [   55.134689] iTCO_wdt: Intel TCO WatchDog Timer Driver v1.01 (11-Nov-2006)
Sep  3 19:54:31 todd-desktop kernel: [   55.134916] iTCO_wdt: No card detected
Sep  3 19:54:31 todd-desktop kernel: [   55.251153] Linux agpgart interface v0.102 (c) Dave Jones
Sep  3 19:54:31 todd-desktop kernel: [   55.322641] agpgart: Detected an Intel 845G Chipset.
Sep  3 19:54:31 todd-desktop kernel: [   55.322782] agpgart: Detected 892K stolen memory.
Sep  3 19:54:31 todd-desktop kernel: [   55.341288] agpgart: AGP aperture is 128M @ 0xf0000000
Sep  3 19:54:31 todd-desktop kernel: [   56.394400] input: PC Speaker as /class/input/input3
Sep  3 19:54:31 todd-desktop kernel: [   56.729681] parport: PnPBIOS parport detected.
Sep  3 19:54:31 todd-desktop kernel: [   56.729741] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
Sep  3 19:54:31 todd-desktop kernel: [   56.986401] usbcore: registered new interface driver snd-usb-audio
Sep  3 19:54:31 todd-desktop kernel: [   57.006414] ACPI: PCI Interrupt 0000:00:1f.5[B] -> GSI 17 (level, low) -> IRQ 20
Sep  3 19:54:31 todd-desktop kernel: [   57.321454] intel8x0_measure_ac97_clock: measured 55009 usecs
Sep  3 19:54:31 todd-desktop kernel: [   57.321460] intel8x0: clocking to 48000
Sep  3 19:54:31 todd-desktop kernel: [   57.591413] fuse init (API version 7.8)
Sep  3 19:54:31 todd-desktop kernel: [   57.628909] lp0: using parport0 (interrupt-driven).
Sep  3 19:54:31 todd-desktop kernel: [   57.691897] Adding 1646620k swap on /dev/disk/by-uuid/4438e43f-27c3-4ff4-a520-53e7c1ceef6c.  Priority:-1 extents:1 across:1646620k
Sep  3 19:54:31 todd-desktop kernel: [   57.876767] EXT3 FS on sda1, internal journal
Sep  3 19:54:31 todd-desktop kernel: [   64.361634] No dock devices found.
Sep  3 19:54:31 todd-desktop kernel: [   64.651944] input: Power Button (FF) as /class/input/input4
Sep  3 19:54:31 todd-desktop kernel: [   64.659746] ACPI: Power Button (FF) [PWRF]
Sep  3 19:54:31 todd-desktop kernel: [   64.713355] input: Power Button (CM) as /class/input/input5
Sep  3 19:54:31 todd-desktop kernel: [   64.721195] ACPI: Power Button (CM) [PWRB]
Sep  3 19:54:31 todd-desktop kernel: [   64.747265] Using specific hotkey driver
Sep  3 19:54:31 todd-desktop kernel: [   64.856131] pcc_acpi: loading...
Sep  3 19:54:35 todd-desktop dhcdbd: Started up.
Sep  3 19:54:35 todd-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Sep  3 19:54:35 todd-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.reason
Sep  3 19:54:36 todd-desktop kernel: [   71.376954] ppdev: user-space parallel port driver
Sep  3 19:54:37 todd-desktop kernel: [   72.172449] [drm] Initialized drm 1.1.0 20060810
Sep  3 19:54:37 todd-desktop kernel: [   72.239874] ACPI: PCI Interrupt 0000:00:02.0[A] -> GSI 16 (level, low) -> IRQ 16
Sep  3 19:54:37 todd-desktop kernel: [   72.241600] [drm] Initialized i915 1.6.0 20060119 on minor 0
Sep  3 19:54:37 todd-desktop hpiod: 1.7.3 accepting connections at 2208... 
Sep  3 19:54:38 todd-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Sep  3 19:54:38 todd-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Sep  3 19:54:38 todd-desktop dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Sep  3 19:54:39 todd-desktop kernel: [   74.151036] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
Sep  3 19:54:39 todd-desktop kernel: [   74.151045] apm: overridden by ACPI.
Sep  3 19:54:39 todd-desktop kernel: [   74.710557] Bluetooth: Core ver 2.11
Sep  3 19:54:39 todd-desktop kernel: [   74.710671] NET: Registered protocol family 31
Sep  3 19:54:39 todd-desktop kernel: [   74.710675] Bluetooth: HCI device and connection manager initialized
Sep  3 19:54:39 todd-desktop kernel: [   74.710682] Bluetooth: HCI socket layer initialized
Sep  3 19:54:39 todd-desktop kernel: [   74.779324] Bluetooth: L2CAP ver 2.8
Sep  3 19:54:39 todd-desktop kernel: [   74.779331] Bluetooth: L2CAP socket layer initialized
Sep  3 19:54:39 todd-desktop kernel: [   74.810145] Bluetooth: RFCOMM socket layer initialized
Sep  3 19:54:39 todd-desktop kernel: [   74.810171] Bluetooth: RFCOMM TTY layer initialized
Sep  3 19:54:39 todd-desktop kernel: [   74.810176] Bluetooth: RFCOMM ver 1.8
Sep  3 19:54:55 todd-desktop gconfd (todd-5435): starting (version 2.18.0.1), pid 5435 user 'todd'
Sep  3 19:54:55 todd-desktop gconfd (todd-5435): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Sep  3 19:54:55 todd-desktop gconfd (todd-5435): Resolved address "xml:readwrite:/home/todd/.gconf" to a writable configuration source at position 1
Sep  3 19:54:55 todd-desktop gconfd (todd-5435): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Sep  3 19:54:55 todd-desktop gconfd (todd-5435): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Sep  3 19:54:55 todd-desktop gconfd (todd-5435): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Sep  3 19:55:05 todd-desktop gconfd (todd-5435): Resolved address "xml:readwrite:/home/todd/.gconf" to a writable configuration source at position 0
Sep  3 20:04:54 todd-desktop kernel: [  687.848980] usb 4-5: new high speed USB device using ehci_hcd and address 4
Sep  3 20:04:54 todd-desktop kernel: [  687.981822] usb 4-5: configuration #1 chosen from 1 choice
todd@todd-desktop:~$ 
todd@todd-desktop:~$

---

### Post by CRCarl on 2007-09-04
The lsusb shows me the vendor and product id, the messages file tells me if there were any errors connecting the device (there were not).

I found a fix in the French language Ubuntu forums :)

[http://www.google.com/translate?u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D1058213&langpair=fr%7Cen&hl=en&ie=UTF8]("http://www.google.com/translate?u=http%3A%2F%2Fforum.ubuntu-fr.org%2Fviewtopic.php%3Fpid%3D1058213&langpair=fr%7Cen&hl=en&ie=UTF8")

Edit this file - 

```
/etc/udev/rules.d
```

Add these lines -

```
# Samsung YP-U3 (finally in short the name of the reader) 
SYSFS {idVendor} == " 04e8 ", SYSFS {idProduct} == " 507d ", SYMLINK+= " libmtp-%k ", MODE= " 666 " 
```

Install gnomad2

```
sudo aptitude install gnomad2
```

You will not be able to use Rhythmbox, you will have to use gnomad2 to manage the device. 

Let us know if that works.

---

### Post by 1002285 on 2007-09-09
I have the same samsung (2 Gb version) and I am not able to copy files to it in Linux. In Gnome, by the way, the copying did not get going at all (it started and froze at "copying fie 1/74" or sth like that), but in KDE, it kind of copied half of the files, but did not show them later, although when attempting to copy again, it asked "do you want to overwrite".

I found this thread here and did this:
```
sudo kate /etc/udev/rules.d/65-libmtp.rules
```
and added the lines you recommended here:
```
# Samsung YP-U3 (finally in short the name of the reader) 
SYSFS {idVendor} == " 04e8 ", SYSFS {idProduct} == " 507d ", SYMLINK+= " libmtp-%k ", MODE= " 666 " 
```

Gnomad2 does not recognize the jukebox and copying is still not possible. It does turn up in the "media". In Windows, the simple copying and pasting worked.

Do I have another problem here?

---

### Post by halw on 2007-09-09
Am trying to set up a Samsung YP-T9J in Ubuntu Dapper. Problem is the is no 65-libmtp.rules file.

Below is the result of lsusb command:

Bus 001 Device 003: ID 04e8:507f Samsung Electronics Co., Ltd
Bus 001 Device 001: ID 0000:0000

Also result of  ls /etc/udev/rules.d
00-init.rules         60-symlinks.rules         85-hwclock.rules
20-names.rules        65-persistent-disk.rules  85-ifupdown.rules
25-iftab.rules        80-programs.rules         85-pcmcia.rules
40-permissions.rules  85-alsa.rules             90-hal.rules
45-libgphoto2.rules   85-hal.rules              90-modprobe.rules
45-libsane.rules      85-hdparm.rules           99-udevmonitor.rules

Suggestions please.

---

### Post by p-w on 2007-09-22
Hi, I have just got a 4Gb Samsung U3 working under kubuntu 7.04 with Amarok, tracks seem to transfer properly.  I added the lines in the post above from Way Too Much Ubuntu to ```
/etc/udev/rules.d/65-libmtp.rules
```  Then I restarted udev ```
sudo /etc/init.d/udev restart
``` Then in Amorak I added a media device.  To do this go to Settings->Configure Amarok->Media Devices.  Click on "Add Device", Select the plugin "MTP Media Device" and enter a name such as "samsung", Click on OK to close the dialogue and add the device, then click OK on the configuration dialogue.  Click on the "Devices" tab on the left had side of the screen and then "Connect" in the toolbar at the top,  You should see the tracks on the mp3 player appear in the window. 

If you do not have Amarok installed (eg if you are running ubuntu rather than kubuntu) then you should be able install it with the command```
sudo apt-get install amarok amarok-engines amarok libxine-extracodecs
```  By default kubuntu does not install the libxine-extracodecs package which is required to play mp3 files so kubuntu users may want to add that.

---

### Post by xtifr on 2007-11-06
I just got one of the YP-U3s--I got it because it said it supported Ogg Vorbis.  Unfortunately, the support is not as good as I'd hoped.  It plays them, and it shows the title and artist while it's playing them, but it files them all as unknown artist and unknown album, and won't display the title unless the track is playing.  Which is just silly.

The device uses Microsoft's "special" Media Transfer Protocol (MTP), which means that support in Linux is lagging, but not completely non-existent (as several above have noted).

The version of libmtp (libmtp5) in Feisty doesn't recognize this player, but the version on my Debian Unstable box (libmtp6) did.  I was able to coax libmtp5 to work by copying over a configuration file from my Debian box, but in the long run, I probably want to either backport libmtp6 or upgrade to Gutsy.  I've also found some bugs in the command line tools included with the library (both versions).

With some hackery, I've managed to get it working pretty well from the command line, but it's a bit tedious, and I don't plan to rest until I've either found or created the tools to integrate it with both Rhythmbox and Nautilus.  (KDE is not allowed near my machines.)  Generic Python support is also in my hopes/plans.

---

### Post by jjmurre on 2007-12-05
Worked for me on Feisty. I did the following:

- sudo apt-get install libmpt5
- changed /etc/udev/rules.d/65-libmtp.rules as indicated above
- sudo apt-get install gnomad2

Although Gnomad2 needs some UI love :-)  I'm happy it works, and very thankfull for the guys that wrote libmtp5.

I did'nt know about this whole MTP stuff, assumed I could just mount the Samsung.
Wikipedia has a nice entry about MTP:

[http://en.wikipedia.org/wiki/Media_Transfer_Protocol](http://en.wikipedia.org/wiki/Media_Transfer_Protocol)

---

### Post by xtifr on 2007-12-05
I did figure out why the oggs I loaded manually weren't showing the title: it's because I was using mtp-sendfile rather than mtp-sendtrack.  I've now created a quick-and-dirty script to load sets of oggs, and it extracts the artist/title/album info from the ogg and passes that to mtp-sendtrack along with the file name.  Works great.

I also tried booting from a Gutsy install disk, and the version of Rhythmbox in Gutsy has mtp support built in!  I'll provide my hacker script if any die-hard Feisty users really want it, but anyone who upgrades to Gutsy (which I'll do soon) shouldn't need it.  The YP-U3 (and probably any similar device) seems to work just great in Gutsy without any additional help or patching required.

---

### Post by badmotor on 2008-02-14
Well thats a shame... because I took it back to the shop and bought a Sony drag-and-drop device. 
That solved it :)

---

### Post by virogenesis1 on 2008-05-20
Mine works now using Gnomad - kickass! Thanks Carl for digging this solution out.

---

