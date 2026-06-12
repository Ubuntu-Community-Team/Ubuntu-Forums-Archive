---
title: "USB external drive + USB audio DAC + audacious"
date: 2009-10-07
forum: Hardware
---

### Post by atchik on 2009-10-07
I am using Ununtu 8.04, 2.6.24-24-generic #1 SMP Sat Aug 22 01:06:14 UTC 2009 i686 GNU/Linux on ASUS A2500H. Recently I have purchased external USB drive  (bytecc ME535ISA) with Seagate 1TB HDD LP). I created reiserFS initially on the drive and it worked ok until I plugged in my USB audio DAC (Trends UD-10.1) and started actually using it with audacious. Somewhere in the middle of playing ape CUE file disk disappeared (while whiting) with badly damaged partition table. I managed to fix it but it happened again. It could happen in a middle of playing or just after USB audio DAC get connected. Almost every time reiserfs got damaged. Few times partition table was damaged as well. After some reading I switched to xfs. The disk still disappears sometimes while audacious is playing either mp3 or ape using USB DAC as output device. However partition table has not been damaged then and xfs recovers automatically after crashes. Then I tried rhythmbox and have not seen any crashes so far. However so far I prefer audacious because of ape and other format support, and I am using USB UD-10.1 for more than year without any significant problem. But I noticed audacious has problem playing specifically CUE files and some other files as well. Sometimes it freezes and needs to be restarted. 

Questions:
  1.Has anyone see this behavior with external USB DAC and USB disk running at the same time? Is it USB driver/module problem?
  2.Or could it be audacious design? Does it handle USB output differently than for example rhythmbox? Rhythmbox plays to default sound card but Audacious output card settings are set within audacious itself.
  
Installed:
  ii  audacious      1.5.1-3~hardy~
  ii  rhythmbox      0.11.5-0ubuntu
   
  lsmod:
  xfs                   571416  1
  reiserfs              239872  0
  snd_usb_audio          83936  2
  snd_usb_lib            18432  1 snd_usb_audio
  snd_hwdep              10500  1 snd_usb_audio
  snd_intel8x0           35356  3
  snd_ac97_codec        101028  1 snd_intel8x0
  ac97_bus                3072  1 snd_ac97_codec
  snd_pcm_oss            42144  0
  snd_mixer_oss          17920  1 snd_pcm_oss
  snd_pcm                78596  5 snd_usb_audio,snd_intel8x0,snd_ac97_codec,snd_pc
  usbcore               146412  8 usb_storage,libusual,usbhid,snd_usb_audio,snd_usb_lib,ehci_hcd,ohci_hcd
  ehci_hcd               37900  0
  ohci_hcd               26640  0
   
lsusb:
Bus 004 Device 017: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 073: ID 0f62:1001 Acrox Technologies Co., Ltd
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 009: ID 08bb:2704 Texas Instruments Japan
Bus 001 Device 001: ID 0000:0000

  dmesg:
      [107355.292034] hub 2-0:1.0: port 1 disabled by hub (EMI?), re-enabling...
  [107355.292048] usb 2-1: USB disconnect, address 46
  [107355.493742] usb 2-1: new low speed USB device using ohci_hcd and address 47
  [107355.708929] usb 2-1: configuration #1 chosen from 1 choice
  [107355.722415] input: Acrox USB & PS/2 Mouse as /devices/pci0000:00/0000:00:03.            1/usb2/2-1/2-1:1.0/input/input56
  [107355.749752] input,hidraw0: USB HID v1.10 Mouse [Acrox USB & PS/2 Mouse] on u            sb-0000:00:03.1-1
  [107521.029009] usb 1-2: new full speed USB device using ohci_hcd and address 6
  [107521.243174] usb 1-2: configuration #1 chosen from 1 choice
  [107521.328212] input: Burr-Brown from TI               USB Audio DAC    as /dev            ices/pci0000:00/0000:00:03.0/usb1/1-2/1-2:1.2/input/input57
  [107521.352918] input,hidraw1: USB HID v1.00 Device [Burr-Brown from TI                           USB Audio DAC   ] on usb-0000:00:03.0-2
  [107559.930254] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107563.404205] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107604.084437] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107607.550400] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107658.644532] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107662.150486] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107708.951125] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107710.726087] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107844.184083] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107846.142930] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107908.074728] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107909.937669] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107946.908027] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107947.927441] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107985.961201] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [107990.446577] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [108125.299750] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [108125.411680] usb 4-6: device descriptor read/64, error -71
  [108125.627563] usb 4-6: device descriptor read/64, error -71
  [108125.843443] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [108125.955362] usb 4-6: device descriptor read/64, error -71
  [108126.171245] usb 4-6: device descriptor read/64, error -71
  [108126.387110] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [108126.794867] usb 4-6: device not accepting address 10, error -71
  [108126.906814] usb 4-6: reset high speed USB device using ehci_hcd and address             10
  [108127.314569] usb 4-6: device not accepting address 10, error -71
  [108127.314742] usb 4-6: USB disconnect, address 10
  [108127.315098] sd 3:0:0:0: Device offlined - not ready after error recovery
  [108127.315640] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRI            VER_OK,SUGGEST_OK
  [108127.315647] end_request: I/O error, dev sdb, sector 1539820463
  [108127.316048] sd 3:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRI            VER_OK,SUGGEST_OK
  [108127.316052] end_request: I/O error, dev sdb, sector 1539820703
  [108127.317012] I/O error in filesystem ("sdb1") meta-data dev sdb1 block 0x3a39            4dbb       ("xlog_iodone") error 5 buf count 3584
  [108127.317025] xfs_force_shutdown(sdb1,0x2) called from line 993 of file /build            /buildd/linux-2.6.24/fs/xfs/xfs_log.c.  Return address = 0xecf0305f
  [108127.317044] Filesystem "sdb1": Log I/O Error Detected.  Shutting down filesy            stem: sdb1
  [108127.317048] Please umount the filesystem, and rectify the problem(s)
  [108127.317475] printk: 765 messages suppressed.
  [108127.317479] Buffer I/O error on device sdb1, logical block 192477914
  [108127.317482] lost page write due to I/O error on sdb1
  [108127.317490] Buffer I/O error on device sdb1, logical block 192477915
  [108127.317492] lost page write due to I/O error on sdb1
   
   
  [108127.326409] xfs_force_shutdown(sdb1,0x1) called from line 420 of file /build            /buildd/linux-2.6.24/fs/xfs/xfs_rw.c.  Return address = 0xecf1d3f3
  [108127.326423] xfs_force_shutdown(sdb1,0x1) called from line 420 of file /build            /buildd/linux-2.6.24/fs/xfs/xfs_rw.c.  Return address = 0xecf1d3f3
   
  [108127.502488] usb 4-6: new high speed USB device using ehci_hcd and address 13
  [108127.618481] usb 4-6: device descriptor read/64, error -71
  [108127.834312] usb 4-6: device descriptor read/64, error -71
  [108128.050154] usb 4-6: new high speed USB device using ehci_hcd and address 14
  [108128.162087] usb 4-6: device descriptor read/64, error -71
  [108128.377995] usb 4-6: device descriptor read/64, error -71
  [108128.593863] usb 4-6: new high speed USB device using ehci_hcd and address 15
  [108129.001583] usb 4-6: device not accepting address 15, error -71
  [108129.113534] usb 4-6: new high speed USB device using ehci_hcd and address 16
  [108129.521280] usb 4-6: device not accepting address 16, error -71
  [108534.816377] usb 4-6: new high speed USB device using ehci_hcd and address 17
  [108534.950211] usb 4-6: configuration #1 chosen from 1 choice
  [108534.981567] scsi4 : SCSI emulation for USB Mass Storage devices
  [108534.983667] usb-storage: device found at 17
  [108534.983676] usb-storage: waiting for device to settle before scanning
  [108539.977604] usb-storage: device scan complete
  [108539.978481] scsi 4:0:0:0: Direct-Access     ST310005 20AS                  P            Q: 0 ANSI: 2 CCS
  [108539.989453] sd 4:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205             MB)
  [108539.991382] sd 4:0:0:0: [sdc] Write Protect is off
  [108539.991390] sd 4:0:0:0: [sdc] Mode Sense: 00 38 00 00
  [108539.991393] sd 4:0:0:0: [sdc] Assuming drive cache: write through
  [108539.992555] sd 4:0:0:0: [sdc] 1953525168 512-byte hardware sectors (1000205             MB)
  [108539.993312] sd 4:0:0:0: [sdc] Write Protect is off
  [108539.993347] sd 4:0:0:0: [sdc] Mode Sense: 00 38 00 00
  [108539.993350] sd 4:0:0:0: [sdc] Assuming drive cache: write through
  [108539.993362]  sdc: sdc1
  [108540.007712] sd 4:0:0:0: [sdc] Attached SCSI disk
  [108540.007776] sd 4:0:0:0: Attached scsi generic sg2 type 0
   
  [109850.634998] Starting XFS recovery on filesystem: sdc1 (logdev: internal)
  [109851.104108] Ending XFS recovery on filesystem: sdc1 (logdev: internal)
---
Thanks, Alex

---

### Post by atchik on 2009-10-18
... it looks like i am talking to myself here... where are the experts, i wonder? ;-) anyway, for a ubumonkeys like myself:
apparrently the reason was found, the problem is kernel bug relates to JM20337 circuitry in the enclosure. Here is some description: [http://bugzilla.kernel.org/show_bug.cgi?id=9638](http://bugzilla.kernel.org/show_bug.cgi?id=9638), solution and HW patch [http://bigacid.wordpress.com/2008/12/08/jm20337-read-data-corruption-solution/](http://bigacid.wordpress.com/2008/12/08/jm20337-read-data-corruption-solution/). Looks like they are talking the right things there: I tried another enclosure based on JM20337 which is  NexStar Hard Drive Dock NST-D100S2 and it works fine.
The bottom line: be careful with enclosures based on JM20337 specifically the old one and from cheap makers like bytecc, quote:
---
[I]Say, the `usn' scsi_io request (easy to issue with
[http://samba.org/~tridge/ctdb/utils/scsi_io/scsi_io.c]("http://samba.org/%7Etridge/ctdb/utils/scsi_io/scsi_io.c")) causes I/O errors on my
JMicron-identified enclosure.  More details at
[https://bugzilla.redhat.com/show_bug.cgi?id=465539](https://bugzilla.redhat.com/show_bug.cgi?id=465539)
t's not surprising that an obscure SCSI command would cause a USB-IDE bridge
to fail.  A lot of those chips aren't terribly high quality; sending them
commands they don't understand is asking for trouble.
Some chips even have trouble with commands they _do_ understand, if the amount
of data asked for isn't exactly right.  In your original example there is an
INQUIRY command asking for 254 bytes.  Plenty of USB-IDE bridges crash if
INQUIRY asks for anything other than 18 bytes.[/I]
---

---

