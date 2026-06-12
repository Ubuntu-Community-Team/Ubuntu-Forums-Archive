---
title: "lucid: usb card handling broken?"
date: 2010-05-08
forum: Hardware
---

### Post by gwing on 2010-05-08
Since upgrading from Jaunty through Karmic to Lucid 10.04 writing files to USB connected SDHC card appears broken. Symptoms:
1) When I write a directory try to the USB card from Ubuntu it appears to be OK. However after I 'safely dismount' the card through gui and remount only the top level directory is visible, all files and folders in subdirectories are missing. Mounding the card on a windows machine also only shows the top level.
2) I test that I can play an avi file on local disk in movie player, all OK. Then copy file to USB (which has to be the root directory of course) and this then fails to play. Copy back to local disk - still refuses to play. Error received= 'GstDecodeBin2: This appears to be a text file'

Some testing from command line (here>= ubuntu local file system):

here>ls -l
total 718168
-rw-r--r-- 1 rob rob 734676992 2010-04-30 23:56 Agora.Cd1-iKA.avi
here>sum ./Agora.Cd1-iKA.avi
56299 717458
here>cp Agora.Cd1-iKA.avi /media/disk/test1.avi
here>echo $?
0                                                                -- so it apparently worked
here>sum /media/disk/test1.avi
54862 717458                                              -- but the checksum doesn't match!
here>sync;sync;sync
here>sum /media/disk/test1.avi
23168 717458                                              -- still no match, but diferent!
here>sync
here>echo $?
0                                                                 -- at least the sync worked
here>sum /media/disk/test1.avi
60229 717458                                              -- different again, but still wrong

At this point I 'safely removed drive' through gui, unplugged and replugged it to remout.

here>sum /media/disk/test1.avi
38392 717458                                              --still wrong
here>sum /media/disk/test1.avi
38392 717458                                  
here>sum /media/disk/test1.avi
38392 717458                                              -- still wrong, but consistent after remount

At this point I tried to play the 'consistently wrong' file but again get 'GstDecodeBin2: This appears to be a text file'

Is this a known issue? Anyone got any ideas how I can get the USB card to work? Note that I have to keep it in DOS format as it is used to interchange files between machines.

Some stuff from 'dmesg':
usb-storage: device found at 5
[89927.079025] usb-storage: waiting for device to settle before scanning
[89932.071216] usb-storage: device scan complete
[89932.159448] scsi 11:0:0:0: Direct-Access     Lexar    CFUDMASD         1000 PQ: 0 ANSI: 0 CCS
[89933.374457] scsi 11:0:0:1: Direct-Access     Lexar    CFUDMASD         1000 PQ: 0 ANSI: 0 CCS
[89933.375054] sd 11:0:0:0: Attached scsi generic sg5 type 0
[89933.378373] sd 11:0:0:1: Attached scsi generic sg6 type 0
[89933.388303] sd 11:0:0:0: [sde] Attached SCSI removable disk
[89933.388925] sd 11:0:0:1: [sdf] 65534976 512-byte logical blocks: (33.5 GB/31.2 GiB)
[89933.389680] sd 11:0:0:1: [sdf] Write Protect is off
[89933.389684] sd 11:0:0:1: [sdf] Mode Sense: 4b 00 00 08
[89933.389688] sd 11:0:0:1: [sdf] Assuming drive cache: write through
[89933.392553] sd 11:0:0:1: [sdf] Assuming drive cache: write through
[89933.392560]  sdf: sdf1
[89933.394929] sd 11:0:0:1: [sdf] Assuming drive cache: write through
[89933.394935] sd 11:0:0:1: [sdf] Attached SCSI removable disk
[115344.696706] UDP: bad checksum. From 87.93.31.183:27184 to 192.168.0.64:61137 ulen 106
[150147.015888] npviewer.bin[18698]: segfault at ff99cd48 ip 00000000ff99cd48 sp 00000000ffbc2b8c error 14
[150778.670042] usb 2-3: USB disconnect, address 5
[150785.190746] usb 2-3: new high speed USB device using ehci_hcd and address 6
[150785.509864] usb 2-3: configuration #1 chosen from 1 choice
[150785.510220] scsi12 : SCSI emulation for USB Mass Storage devices
[150785.510534] usb-storage: device found at 6
[150785.510537] usb-storage: waiting for device to settle before scanning
[150790.510164] usb-storage: device scan complete
[150790.598272] scsi 12:0:0:0: Direct-Access     Lexar    CFUDMASD         1000 PQ: 0 ANSI: 0 CCS
[150791.813152] scsi 12:0:0:1: Direct-Access     Lexar    CFUDMASD         1000 PQ: 0 ANSI: 0 CCS
[150791.813703] sd 12:0:0:0: Attached scsi generic sg5 type 0
[150791.813866] sd 12:0:0:1: Attached scsi generic sg6 type 0
[150791.822706] sd 12:0:0:0: [sde] Attached SCSI removable disk
[150791.830640] sd 12:0:0:1: [sdf] 65534976 512-byte logical blocks: (33.5 GB/31.2 GiB)
[150791.831506] sd 12:0:0:1: [sdf] Write Protect is off
[150791.831510] sd 12:0:0:1: [sdf] Mode Sense: 4b 00 00 08
[150791.831513] sd 12:0:0:1: [sdf] Assuming drive cache: write through
[150791.834507] sd 12:0:0:1: [sdf] Assuming drive cache: write through
[150791.834514]  sdf: sdf1
[150791.837607] sd 12:0:0:1: [sdf] Assuming drive cache: write through
[150791.837614] sd 12:0:0:1: [sdf] Attached SCSI removable disk
here>

---

