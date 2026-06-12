---
title: "external harddrive keeps unmounting"
date: 2012-06-17
forum: Hardware
---

### Post by RyanGT on 2012-06-17
I just got a new harddrive and enclosure for Father's Day.  I formatted it as one large (1 TB) ext4 partition using gparted.  I then copied all of our pictures onto it (I want to use it to back up our family pictures).  I copied 150 GB of pictures onto the drive in two pasting operations.  One of the pastes took 40+ minutes, but both seemed to finish just fine.  I want to use unison to keep this backup drive in sync with the internal drive where we store our family photos.  During long unison syncs, the drive consistently unmounts itself and 10 or so minutes.  Here is the relevant section of /var/log/syslog:


Jun 17 20:40:26 AM2 kernel: [ 8473.532069] usb 1-3: new high-speed USB device number 17 using ehci_hcd
Jun 17 20:40:26 AM2 kernel: [ 8473.666094] scsi10 : usb-storage 1-3:1.0
Jun 17 20:40:26 AM2 mtp-probe: checking bus 1, device 17: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3"
Jun 17 20:40:26 AM2 mtp-probe: bus: 1, device: 17 was not an MTP device
Jun 17 20:40:27 AM2 kernel: [ 8474.664840] scsi 10:0:0:0: Direct-Access     WDC WD10 02FAEX-00Y9A0         PQ: 0 ANSI: 2 CCS
Jun 17 20:40:27 AM2 kernel: [ 8474.666493] sd 10:0:0:0: Attached scsi generic sg4 type 0
Jun 17 20:40:27 AM2 kernel: [ 8474.895151] sd 10:0:0:0: [sdd] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
Jun 17 20:40:27 AM2 kernel: [ 8474.895874] sd 10:0:0:0: [sdd] Write Protect is off
Jun 17 20:40:27 AM2 kernel: [ 8474.895882] sd 10:0:0:0: [sdd] Mode Sense: 34 00 00 00
Jun 17 20:40:27 AM2 kernel: [ 8474.896629] sd 10:0:0:0: [sdd] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
Jun 17 20:40:27 AM2 kernel: [ 8474.918739]  sdd: sdd1
Jun 17 20:40:27 AM2 kernel: [ 8474.922496] sd 10:0:0:0: [sdd] Attached SCSI disk
Jun 17 20:40:27 AM2 kernel: [ 8475.390341] EXT4-fs (sdd1): recovery complete
Jun 17 20:40:27 AM2 kernel: [ 8475.418542] EXT4-fs (sdd1): mounted filesystem with ordered data mode. Opts: (null)
Jun 17 20:49:46 AM2 kernel: [ 9034.128065] usb 1-3: reset high-speed USB device number 17 using ehci_hcd
Jun 17 20:49:46 AM2 kernel: [ 9034.261121] usb 1-3: device firmware changed
Jun 17 20:49:46 AM2 kernel: [ 9034.261175] usb 1-3: USB disconnect, device number 17
Jun 17 20:49:46 AM2 kernel: [ 9034.261338] sd 10:0:0:0: Device offlined - not ready after error recovery
Jun 17 20:49:46 AM2 kernel: [ 9034.416098] usb 1-3: new high-speed USB device number 18 using ehci_hcd
Jun 17 20:49:47 AM2 kernel: [ 9034.558314] scsi11 : usb-storage 1-3:1.0
Jun 17 20:49:47 AM2 mtp-probe: checking bus 1, device 18: "/sys/devices/pci0000:00/0000:00:12.2/usb1/1-3"
Jun 17 20:49:47 AM2 mtp-probe: bus: 1, device: 18 was not an MTP device
Jun 17 20:50:09 AM2 kernel: [ 9057.168081] usb 1-3: reset high-speed USB device number 18 using ehci_hcd
Jun 17 20:50:19 AM2 kernel: [ 9067.412239] usb 1-3: reset high-speed USB device number 18 using ehci_hcd
Jun 17 20:50:25 AM2 kernel: [ 9072.656072] usb 1-3: reset high-speed USB device number 18 using ehci_hcd
Jun 17 20:50:25 AM2 kernel: [ 9072.792054] usb 1-3: device descriptor read/64, error -71
Jun 17 20:50:30 AM2 kernel: [ 9078.024057] usb 1-3: device descriptor read/64, error -110
Jun 17 20:50:30 AM2 kernel: [ 9078.240066] usb 1-3: reset high-speed USB device number 18 using ehci_hcd
Jun 17 20:50:30 AM2 kernel: [ 9078.376051] usb 1-3: device descriptor read/64, error -71
Jun 17 20:50:31 AM2 kernel: [ 9078.616050] usb 1-3: device descriptor read/64, error -71
Jun 17 20:50:31 AM2 kernel: [ 9078.832075] usb 1-3: reset high-speed USB device number 18 using ehci_hcd
Jun 17 20:50:31 AM2 kernel: [ 9079.256053] usb 1-3: device not accepting address 18, error -71
Jun 17 20:50:31 AM2 kernel: [ 9079.368075] usb 1-3: reset high-speed USB device number 18 using ehci_hcd
Jun 17 20:50:32 AM2 kernel: [ 9079.792043] usb 1-3: device not accepting address 18, error -71
Jun 17 20:50:32 AM2 kernel: [ 9079.792089] scsi 11:0:0:0: Device offlined - not ready after error recovery
Jun 17 20:50:32 AM2 kernel: [ 9079.792124] usb 1-3: USB disconnect, device number 18
Jun 17 20:50:32 AM2 kernel: [ 9079.908071] usb 1-3: new high-speed USB device number 19 using ehci_hcd
Jun 17 20:50:32 AM2 kernel: [ 9080.044058] usb 1-3: device descriptor read/64, error -71
Jun 17 20:50:32 AM2 kernel: [ 9080.284045] usb 1-3: device descriptor read/64, error -71
Jun 17 20:50:32 AM2 kernel: [ 9080.500082] usb 1-3: new high-speed USB device number 20 using ehci_hcd
Jun 17 20:50:33 AM2 kernel: [ 9080.636055] usb 1-3: device descriptor read/64, error -71
Jun 17 20:50:33 AM2 kernel: [ 9080.876052] usb 1-3: device descriptor read/64, error -71
Jun 17 20:50:33 AM2 kernel: [ 9081.092052] usb 1-3: new high-speed USB device number 21 using ehci_hcd
Jun 17 20:50:33 AM2 kernel: [ 9081.516043] usb 1-3: device not accepting address 21, error -71
Jun 17 20:50:34 AM2 kernel: [ 9081.628052] usb 1-3: new high-speed USB device number 22 using ehci_hcd
Jun 17 20:50:34 AM2 kernel: [ 9082.052054] usb 1-3: device not accepting address 22, error -71
Jun 17 20:50:34 AM2 kernel: [ 9082.052092] hub 1-0:1.0: unable to enumerate USB device on port 3
Jun 17 20:50:34 AM2 kernel: [ 9082.456047] usb 3-3: new full-speed USB device number 11 using ohci_hcd
Jun 17 20:50:35 AM2 kernel: [ 9082.596076] usb 3-3: device descriptor read/64, error -62
Jun 17 20:50:35 AM2 kernel: [ 9082.840054] usb 3-3: device descriptor read/64, error -62
Jun 17 20:50:35 AM2 kernel: [ 9083.080067] usb 3-3: new full-speed USB device number 12 using ohci_hcd
Jun 17 20:50:35 AM2 kernel: [ 9083.220060] usb 3-3: device descriptor read/64, error -62
Jun 17 20:50:35 AM2 kernel: [ 9083.464060] usb 3-3: device descriptor read/64, error -62
Jun 17 20:50:36 AM2 kernel: [ 9083.704068] usb 3-3: new full-speed USB device number 13 using ohci_hcd
Jun 17 20:50:36 AM2 kernel: [ 9084.112070] usb 3-3: device not accepting address 13, error -62
Jun 17 20:50:36 AM2 kernel: [ 9084.248059] usb 3-3: new full-speed USB device number 14 using ohci_hcd
Jun 17 20:50:37 AM2 kernel: [ 9084.656055] usb 3-3: device not accepting address 14, error -62
Jun 17 20:50:37 AM2 kernel: [ 9084.656109] hub 3-0:1.0: unable to enumerate USB device on port 3
Jun 17 20:51:36 AM2 kernel: [ 9143.642399] [drm] nouveau 0000:01:00.0: Setting dpms mode 3 on vga encoder (output 0)
Jun 17 21:10:00 AM2 kernel: [10247.646765] [drm] nouveau 0000:01:00.0: Setting dpms mode 0 on vga encoder (output 0)

The drive seems to mount fine, but then something happens after about 9 minutes.  Any ideas about what the root issue is?  If either the harddrive or the enclosure is defective, any guess as to which I should return?

Thanks,

Ryan

---

### Post by RyanGT on 2012-06-18
I sort of have a solution but would appreciate feedback about whether or not there is a better way.  Another Ubuntu user commented on the newegg feedback page that he had a problem when the drive would spin down.  Apparently either the drive or the enclosure was hard wired to spin down after 10 minutes of inactivity.  

So, he wrote a script to touch a temp file on the drive every minute.  I translated it to Python and set it to touch the file every 3 minutes.  It seems to work fine.  Given that I won't leave the drive on all that much, touching a temp file once every 3 minutes doesn't seem like it would be bad for the life of the drive, but I have to remember to run the script when I turn the drive on.  

Can anyone think of a better solution?  Does this seem like a bad idea?  Can anyone recommend an enclosure that doesn't have this problem?  (I bought the highest rated USB 2.0/eSATA one on newegg).

Thanks,

Ryan

---

### Post by steeldriver on 2012-06-18
Is this a WDC Green drive? if so there is a known issue with the idle timeout / intellipark - it definitely causes problems with raid, I don't know if it would do so during a unison based sync

If that *is* the issue there is a more elegant fix than your 'keep alive' write jobs - see here:

[http://www.storagereview.com/how_stop_excessive_load_cycles_western_digital_2tb_caviar_green_wd20ears_wdidle3](http://www.storagereview.com/how_stop_excessive_load_cycles_western_digital_2tb_caviar_green_wd20ears_wdidle3)

[http://support.wdc.com/product/download.asp?groupid=609&sid=113](http://support.wdc.com/product/download.asp?groupid=609&sid=113)

[http://idle3-tools.sourceforge.net/](http://idle3-tools.sourceforge.net/)

The idle3-tools solution worked for me.

---

### Post by RyanGT on 2012-06-18
Thanks for your quick and thoughtful response.

It is a WDC **BLACK** drive that isn't supposed to do this.  To check if it is the enclosure or the drive, I swapped the drive with one that was internal (WDC BLUE).  The one in the enclosure has the issue and the one that is internal does not (even after I switch them).  

So, I am glad to look into those suggestions, but if the issue is the enclosure, do you think those will work for me?

Thanks,

Ryan

---

### Post by steeldriver on 2012-06-19
It sounds like you've isolated it to an issue with the enclosure not the drive - afaik the WDC Black drives don't have the same Intellipark behavior as the Greens so the links I posted won't be relevant anyhow

Maybe there's a way to configure the enclosure's power down behavior?

---

