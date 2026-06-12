---
title: "USB Reset with External Hard drive"
date: 2008-05-01
forum: Hardware
---

### Post by argosreality on 2008-05-01
Let me preface this by saying: atleast my fears that the drive is dead don't appear to have been correct. Apparently, Linux either still really hates Seagate FreeAgent drives (I'd already previously delt with the sleep issue) or else I've run into something unique with my setup. 

Basically, my 320 Seagate FreeAgent drive (which is currently connected to the mac being backed up) will disconnect from Hardy if I so much as sneeze at it. Whether I'm attempting to scan the mp3's on it and build a rythmbox library or trying to transfer a 1Gb zip file; it disconnects. Even browsing the drive in Nautilus disconnects it. The worst part is the drive doesn't come back. Can't even remount it.

Here's a portion of the output from syslog ```

May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars hald[5288]: forcibly attempting to lazy unmount /dev/sdb1 as enclosing drive was disconnected
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_attr_pread: ntfs_pread failed: Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: Error reading $Mft record(s): Input/output error
May  1 20:31:59 mars ntfs-3g[6162]: ntfs_mft_record_read failed: Input/output error
May  1 20:31:59 mars hald: unmounted /dev/sdb1 from '/media/FreeAgent Drive' on behalf of uid 0
May  1 20:31:59 mars NetworkManager: <debug> [1209688319.338777] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/volume_uuid_6AE86A25E869EFAD'). 
May  1 20:31:59 mars NetworkManager: <debug> [1209688319.339581] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/storage_serial_Seagate_FreeAgentDesktop_6QF21118_0_0'). 
May  1 20:31:59 mars NetworkManager: <debug> [1209688319.339807] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________6QF21118_if0_scsi_host_scsi_device_lun0'). 
May  1 20:31:59 mars NetworkManager: <debug> [1209688319.341133] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________6QF21118_if0_scsi_host'). 
May  1 20:31:59 mars NetworkManager: <debug> [1209688319.344557] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________6QF21118_if0'). 
May  1 20:31:59 mars NetworkManager: <debug> [1209688319.344681] nm_hal_device_removed(): Device removed (hal udi is '/org/freedesktop/Hal/devices/usb_device_bc2_3000_____________6QF21118'). 
May  1 20:31:59 mars kernel: [  440.192630] usb 6-4: new high speed USB device using ehci_hcd and address 7
May  1 20:32:14 mars kernel: [  449.166568] usb 6-4: device descriptor read/64, error -110
May  1 20:32:29 mars kernel: [  457.069534] usb 6-4: device descriptor read/64, error -110
May  1 20:32:29 mars kernel: [  457.172002] usb 6-4: new high speed USB device using ehci_hcd and address 8
May  1 20:32:45 mars kernel: [  468.601550] usb 6-4: device descriptor read/64, error -110
May  1 20:33:00 mars kernel: [  475.996408] usb 6-4: device descriptor read/64, error -110
May  1 20:33:00 mars kernel: [  476.099840] usb 6-4: new high speed USB device using ehci_hcd and address 9
May  1 20:33:11 mars kernel: [  481.059507] usb 6-4: device not accepting address 9, error -110
May  1 20:33:11 mars kernel: [  481.112776] usb 6-4: new high speed USB device using ehci_hcd and address 10
May  1 20:33:21 mars kernel: [  486.074337] usb 6-4: device not accepting address 10, error -110
May  1 20:34:55 mars kernel: [  534.900439] usb 6-4: new high speed USB device using ehci_hcd and address 11
May  1 20:35:10 mars kernel: [  544.500727] usb 6-4: device descriptor read/64, error -110
May  1 20:35:25 mars kernel: [  553.838485] usb 6-4: device descriptor read/64, error -110
May  1 20:35:25 mars kernel: [  553.941221] usb 6-4: new high speed USB device using ehci_hcd and address 12
May  1 20:35:40 mars kernel: [  561.145756] usb 6-4: device descriptor read/64, error -110
May  1 20:35:56 mars kernel: [  568.399761] usb 6-4: device descriptor read/64, error -110
May  1 20:35:56 mars kernel: [  568.502492] usb 6-4: new high speed USB device using ehci_hcd and address 13
May  1 20:36:06 mars kernel: [  573.464052] usb 6-4: device not accepting address 13, error -110
May  1 20:36:06 mars kernel: [  573.517322] usb 6-4: new high speed USB device using ehci_hcd and address 14
May  1 20:36:17 mars kernel: [  578.478879] usb 6-4: device not accepting address 14, error -110
```

Whereas this is the output from dmesg from the same time```

May  1 20:25:59 mars kernel: [  188.325396] hda-intel: Invalid position buffer, using LPIB read method instead.
May  1 20:26:07 mars pulseaudio[5869]: alsa-util.c: Device hw:1 doesn't support 44100 Hz, changed to 16000 Hz.
May  1 20:26:07 mars pulseaudio[5869]: alsa-util.c: Device hw:1 doesn't support 2 channels, changed to 1.
May  1 20:30:37 mars kernel: [  391.142757] usb 6-4: reset high speed USB device using ehci_hcd and address 5
May  1 20:31:07 mars kernel: [  408.085156] usb 6-4: reset high speed USB device using ehci_hcd and address 5
May  1 20:31:38 mars kernel: [  427.587025] usb 6-4: reset high speed USB device using ehci_hcd and address 5
May  1 20:31:48 mars kernel: [  433.400714] usb 6-4: reset high speed USB device using ehci_hcd and address 5
May  1 20:31:59 mars kernel: [  440.128856] usb 6-4: USB disconnect, address 5
May  1 20:31:59 mars kernel: [  440.129122] sd 4:0:0:0: Device offlined - not ready after error recovery
May  1 20:31:59 mars kernel: [  440.129244] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
May  1 20:31:59 mars kernel: [  440.129248] end_request: I/O error, dev sdb, sector 451464127
May  1 20:31:59 mars kernel: [  440.129267] sd 4:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK,SUGGEST_OK
May  1 20:31:59 mars kernel: [  440.129270] end_request: I/O error, dev sdb, sector 451464135
May  1 20:31:59 mars kernel: [  440.130997] lost page write due to I/O error on sdb1
May  1 20:31:59 mars kernel: [  440.131008] lost page write due to I/O error on sdb1
May  1 20:31:59 mars kernel: [  440.131013] lost page write due to I/O error on sdb1
May  1 20:31:59 mars kernel: [  440.131018] lost page write due to I/O error on sdb1
May  1 20:31:59 mars kernel: [  440.131024] lost page write due to I/O error on sdb1
May  1 20:31:59 mars kernel: [  440.131031] lost page write due to I/O error on sdb1
May  1 20:31:59 mars kernel: [  440.192630] usb 6-4: new high speed USB device using ehci_hcd and address 7
May  1 20:32:29 mars kernel: [  457.172002] usb 6-4: new high speed USB device using ehci_hcd and address 8
May  1 20:33:00 mars kernel: [  476.099840] usb 6-4: new high speed USB device using ehci_hcd and address 9
May  1 20:33:11 mars kernel: [  481.112776] usb 6-4: new high speed USB device using ehci_hcd and address 10
May  1 20:34:55 mars kernel: [  534.900439] usb 6-4: new high speed USB device using ehci_hcd and address 11
May  1 20:35:25 mars kernel: [  553.941221] usb 6-4: new high speed USB device using ehci_hcd and address 12
May  1 20:35:56 mars kernel: [  568.502492] usb 6-4: new high speed USB device using ehci_hcd and address 13
May  1 20:36:06 mars kernel: [  573.517322] usb 6-4: new high speed USB device using ehci_hcd and address 14
```

other misc info```
Linux mars 2.6.24-16-generic #1 SMP Thu Apr 10 13:23:42 UTC 2008 i686 GNU/Linux
```

Otherwise its a bone stock Hardy install running on an M2A-VM ATI based board with 3Gb of memory. I know the southbridge of this board has some issues with USB transfer speeds but I never had any problems previously with disconnects in Linux or XP/Vista

Any suggestions?

---

### Post by argosreality on 2008-05-03
No one else is seeing this?

---

### Post by notzed on 2008-06-09
FWIW I'm having the exact same problem since 'upgrading' to 8.04 - on a thinkpad t40.  The hdd is a western digital in my case.  It always worked fine with the 7.x I had before, and works fine on a ps3, and on a desktop box that has fedora 9.

It sometimes takes ages to mount and will drop out by itself or when using it.  If I unplug the usb and power-cycle the external drive it will sometimes re-mount, but it wont otherwise.

---

### Post by Matoridi on 2008-11-03
Hello

I don't know if this is related to your problem, but I have a Seagate FreeAgent too, and found this to be useful :

[http://ubuntuforums.org/showthread.php?t=494673&highlight=seagate+freeagent]("http://ubuntuforums.org/showthread.php?t=494673&highlight=seagate+freeagent") 

Hope this helps


PS.: There seems to be a bug in Hardy, though, since I have a new problem: all my USB drives sometimes unmount themselves...  Launchpad has something on this, but no progress so far to solve it.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206125]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206125")

---

### Post by kgr132 on 2009-01-12
I had a similar problem with a FreeAgent Go drive. I fixed it by disabling the drive's standby mode. The code below assumes your drive is /dev/sdb. Adjust that as necessary.

make sure you have the sdparm package installed.

Usage: sdparm [--all] [--clear=STR] [--command=CMD] [--dbd] [--defaults]
              [--dummy] [--flexible] [--get=STR] [--help] [--hex] [--inquiry]
              [--long] [--page=PG[,SPG]] [--quiet] [--save] [--set=STR]
              [--six] [--transport=TN] [--vendor=VN] [--verbose] [--version]
              DEVICE

       sdparm --enumerate [--all] [--inquiry] [--long] [--page=PG[,SPG]]
              [--transport=TN] [--vendor=VN]
  where:
    --all | -a            list all known attributes for given device
    --clear=STR | -c STR    clear (zero) attribute value(s)
    --command=CMD | -C CMD    perform CMD (e.g. 'eject')
    --dbd | -B            set DBD bit in mode sense cdb
    --defaults | -D       set a mode page to its default values
    --dummy | -d          don't write back modified mode page
    --enumerate | -e      list known pages and attributes (ignore device)
    --flexible | -f       compensate for common errors, relax some checks
    --get=STR | -g STR    get (fetch) attribute value(s)
    --help | -h           print out usage message
    --hex | -H            output in hex rather than name/value pairs
    --inquiry | -i        output INQUIRY VPD page(s) (def: mode page(s))
    --long | -l           add description to attribute output
    --page=PG[,SPG] | -p PG[,SPG]    page (and optionally subpage) number
                          [or abbrev] to output, change or enumerate
    --quiet | -q          suppress device vendor/product/revision string line
    --save | -S           place mode changes in saved page as well
    --set=STR | -s STR    set attribute value(s)
    --six | -6            use 6 byte SCSI mode cdbs (def: 10 byte)
    --transport=TN | -t TN    transport protocol number [or abbrev]
    --vendor=VN | -M VN    vendor (manufacturer) number [or abbrev]
    --verbose | -v        increase verbosity
    --version | -V        print version string and exit

CODE:
# sudo sdparm -al /dev/sdb 
    /dev/sdb: Seagate   FreeAgent Go  100F
    Direct access device specific parameters: WP=0  DPOFUA=0
Power condition [po] mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]  Idle timer active
  STANDBY     1  [cha: y, def:  1, sav:  1]  Standby timer active
  ICT         0  [cha: n, def:  0, sav:  0]  Idle condition timer (100 ms)
  SCT       2400  [cha: y, def:2400, sav:2400]  Standby condition timer (100 ms)

# sudo sdparm --clear STANDBY -6 /dev/sdb 
    /dev/sdb: Seagate   FreeAgent Go  100F

# sudo sdparm -al /dev/sdb 
    /dev/sdb: Seagate   FreeAgent Go  100F
    Direct access device specific parameters: WP=0  DPOFUA=0
Power condition [po] mode page:
  IDLE        0  [cha: n, def:  0, sav:  0]  Idle timer active
  STANDBY     0  [cha: n, def:  1, sav:  0]  Standby timer active
  ICT         0  [cha: n, def:  0, sav:  0]  Idle condition timer (100 ms)
  SCT         0  [cha: n, def:2400, sav:  0]  Standby condition timer (100 ms)

# sudo sdparm --save -6 /dev/sdb
    /dev/sdb: Seagate   FreeAgent Go  100F

---

### Post by birddog165 on 2009-01-26
I'm having the same problem as this guy.
My thread is here: [http://ubuntuforums.org/showthread.php?t=1049488](http://ubuntuforums.org/showthread.php?t=1049488)
I'm gonna try your solution and see how it works

---

### Post by birddog165 on 2009-01-28
Just a quick question? By any chance do you have any virtualization software (ie. Parallels, VirtualBox, etc) installed?

---

### Post by Excedio on 2009-01-29
I do. I have the Sun xVM VirtualBox.

---

### Post by birddog165 on 2009-01-29
As do I. And I'll tell you what. I don't remember any problems before I installed that.

---

