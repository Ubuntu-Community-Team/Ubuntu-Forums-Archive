---
title: "Blackberry with mini-SD no longer automounts."
date: 2008-07-17
forum: Hardware
---

### Post by SeanJFraley on 2008-07-17
I have a Blackberry Pearl with an internal mini-SD card that mounted fine about three or four weeks ago, but now no longer seems to be detected properly when I connect it.  The last time I connected it to my PC it was detected fine, the pop-up appeared in KDE saying that it had discovered new removable media and asking if I wanted to mount it, and it mounted fine as sdb1.  Now, plugging it in seems to do nothing.  If I go into the System Settings option on the K menu and look at the Disks & Filesystems section the Blackberry is listed (as /dev/sdb), but no options are available to mount it or edit it's mount options.  There have been some updates to the kernel and some other packages since then.  Does anyone have a clue as to what can be done to get this fixed since I really would like to transfer some photos of the phone and get some new mp3s on there.

---

### Post by Carbunkel on 2008-08-15
I'm actually having a similar problem with my pearl in gnome, except mine stays mounted for about 5 minutes, then it can't detect it at all. And now it says that it can't even charge it. Moving around my media just corrupts my media card... And this only started happening a week after I was doing it. Do I need any special software or something? I hope this gets you a reply as well.

---

### Post by CAE2685 on 2008-12-06
I was having the same problem with my 8330 Curve. On the BB, go to Options --> Media Card --> Mass Storage Mode Support and set it to "On" or "Prompt".

It prompted me to start Mass Storage Mode, and immediately showed up as a drive in Ubuntu.

---

### Post by ee19921 on 2008-12-18
I have Blackberry Pearl. Same problem here! Automount worked like a charm last time I noticed(few weeks back I guess). Now I have to manually auto mount to make it work. 

I am also posting the system log, if it helps!

```

Dec 18 11:48:54 klaptop kernel: [192749.308060] usb 5-2: new full speed USB device using uhci_hcd and address 9
Dec 18 11:48:54 klaptop kernel: [192749.498363] usb 5-2: configuration #1 chosen from 1 choice
Dec 18 11:48:54 klaptop kernel: [192749.504519] scsi10 : SCSI emulation for USB Mass Storage devices
Dec 18 11:48:54 klaptop kernel: [192749.507001] usb-storage: device found at 9
Dec 18 11:48:54 klaptop kernel: [192749.507012] usb-storage: waiting for device to settle before scanning
Dec 18 11:48:59 klaptop kernel: [192754.505350] usb-storage: device scan complete
Dec 18 11:48:59 klaptop kernel: [192754.709580] scsi 10:0:0:0: Direct-Access     RIM      BlackBerry SD    0001 PQ: 0 ANSI: 4 CCS
Dec 18 11:48:59 klaptop kernel: [192754.732300] sd 10:0:0:0: [sdb] 3987456 512-byte hardware sectors (2042 MB)
Dec 18 11:48:59 klaptop kernel: [192754.739302] sd 10:0:0:0: [sdb] Write Protect is off
Dec 18 11:48:59 klaptop kernel: [192754.739318] sd 10:0:0:0: [sdb] Mode Sense: 43 00 00 53
Dec 18 11:48:59 klaptop kernel: [192754.739325] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Dec 18 11:48:59 klaptop kernel: [192754.749296] sd 10:0:0:0: [sdb] 3987456 512-byte hardware sectors (2042 MB)
Dec 18 11:48:59 klaptop kernel: [192754.757204] sd 10:0:0:0: [sdb] Write Protect is off
Dec 18 11:48:59 klaptop kernel: [192754.757218] sd 10:0:0:0: [sdb] Mode Sense: 43 00 00 53
Dec 18 11:48:59 klaptop kernel: [192754.757224] sd 10:0:0:0: [sdb] Assuming drive cache: write through
Dec 18 11:48:59 klaptop kernel: [192754.761814]  sdb:
Dec 18 11:48:59 klaptop kernel: [192754.771431] sd 10:0:0:0: [sdb] Attached SCSI removable disk
Dec 18 11:48:59 klaptop kernel: [192754.773331] sd 10:0:0:0: Attached scsi generic sg2 type 0

```

any help is appreciated!

---

### Post by High Roller on 2008-12-29
I have the same problem.  I only get to mount it once and then I have to reboot.  Sometimes it doesn't mount at all.  Sometimes I end up with an orphaned icon on the desktop that I can't "unmount" no matter what.

---

### Post by ee19921 on 2009-03-19
Now out of nowhere, auto mount has started to work.

---

