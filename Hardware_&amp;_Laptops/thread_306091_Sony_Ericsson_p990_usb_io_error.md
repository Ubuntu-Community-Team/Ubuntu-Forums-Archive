---
title: "Sony Ericsson p990 usb i/o error"
date: 2006-11-24
forum: Hardware &amp; Laptops
---

### Post by johnwards on 2006-11-24
Hi,

I am trying to connect my shiney new p990 using my USB cable. I don't have bluetooth on my computer.

I lsusb I get this..

```

Bus 005 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 116: ID 0fce:e030 Sony Ericsson Mobile Communications AB 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 005: ID 045e:009d Microsoft Corp. 
Bus 001 Device 001: ID 0000:0000

```

If I dmesg I get this:
```

[18589819.732000] usb 4-1: new full speed USB device using uhci_hcd and address 116
[18589819.912000] usb 4-1: configuration #1 chosen from 1 choice
[18589819.916000] scsi10 : SCSI emulation for USB Mass Storage devices
[18589819.916000] usb-storage: device found at 116
[18589819.916000] usb-storage: waiting for device to settle before scanning
[18589824.920000] usb-storage: device scan complete
[18589824.924000]   Vendor:           Model: P990i             Rev: 1.0 
[18589824.924000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[18589824.936000] SCSI device sdc: 1959826 512-byte hdwr sectors (1003 MB)
[18589824.936000] sdc: Write Protect is off
[18589824.936000] sdc: Mode Sense: 03 00 00 00
[18589824.936000] sdc: assuming drive cache: write through
[18589824.948000] SCSI device sdc: 1959826 512-byte hdwr sectors (1003 MB)
[18589824.952000] sdc: Write Protect is off
[18589824.952000] sdc: Mode Sense: 03 00 00 00
[18589824.952000] sdc: assuming drive cache: write through
[18589824.952000]  sdc:
[18589824.964000] sd 10:0:0:0: Attached scsi removable disk sdc
[18589824.964000] sd 10:0:0:0: Attached scsi generic sg2 type 0
[18589825.164000] end_request: I/O error, dev sdc, sector 1959824
[18589825.164000] printk: 249 messages suppressed.
[18589825.164000] Buffer I/O error on device sdc, logical block 979912
[18589825.172000] end_request: I/O error, dev sdc, sector 1959824
[18589825.172000] Buffer I/O error on device sdc, logical block 979912
[18589825.176000] end_request: I/O error, dev sdc, sector 1959824
[18589825.176000] Buffer I/O error on device sdc, logical block 979912
[18589825.184000] end_request: I/O error, dev sdc, sector 1959824
[18589825.184000] Buffer I/O error on device sdc, logical block 979912
[18589825.188000] end_request: I/O error, dev sdc, sector 1959824
[18589825.188000] Buffer I/O error on device sdc, logical block 979912
[18589825.196000] end_request: I/O error, dev sdc, sector 1959824
[18589825.196000] Buffer I/O error on device sdc, logical block 979912
[18589825.204000] end_request: I/O error, dev sdc, sector 1959760
[18589825.204000] Buffer I/O error on device sdc, logical block 979880
[18589825.204000] Buffer I/O error on device sdc, logical block 979881
[18589825.204000] Buffer I/O error on device sdc, logical block 979882
[18589825.204000] Buffer I/O error on device sdc, logical block 979883
[18589825.212000] end_request: I/O error, dev sdc, sector 1959760
[18589825.224000] end_request: I/O error, dev sdc, sector 1959808
[18589825.232000] end_request: I/O error, dev sdc, sector 1959808
[18589825.240000] end_request: I/O error, dev sdc, sector 0
[18589825.252000] end_request: I/O error, dev sdc, sector 0
[18589825.260000] end_request: I/O error, dev sdc, sector 0
[18589825.284000] end_request: I/O error, dev sdc, sector 0
[18589825.296000] end_request: I/O error, dev sdc, sector 0
[18589825.304000] end_request: I/O error, dev sdc, sector 0
[18589825.316000] end_request: I/O error, dev sdc, sector 0
[18589825.432000] end_request: I/O error, dev sdc, sector 40
[18589825.440000] end_request: I/O error, dev sdc, sector 0
[18589825.452000] end_request: I/O error, dev sdc, sector 0
[18589825.460000] end_request: I/O error, dev sdc, sector 0
[18589825.468000] end_request: I/O error, dev sdc, sector 0
[18589825.476000] end_request: I/O error, dev sdc, sector 0
[18589825.488000] end_request: I/O error, dev sdc, sector 0
[18589825.500000] end_request: I/O error, dev sdc, sector 0
[18589825.508000] end_request: I/O error, dev sdc, sector 0
[18589825.516000] end_request: I/O error, dev sdc, sector 0
[18589825.524000] end_request: I/O error, dev sdc, sector 0
[18589825.536000] end_request: I/O error, dev sdc, sector 0
[18589825.544000] end_request: I/O error, dev sdc, sector 0
[18589825.556000] end_request: I/O error, dev sdc, sector 0
[18589825.564000] end_request: I/O error, dev sdc, sector 0
[18589825.572000] end_request: I/O error, dev sdc, sector 0
[18589825.584000] end_request: I/O error, dev sdc, sector 0
[18589825.592000] end_request: I/O error, dev sdc, sector 0
[18589825.600000] end_request: I/O error, dev sdc, sector 0

```

If I take out my memory card I get this...

```

[18590073.292000] usb 4-1: new full speed USB device using uhci_hcd and address 117
[18590073.476000] usb 4-1: configuration #1 chosen from 1 choice
[18590073.480000] scsi11 : SCSI emulation for USB Mass Storage devices
[18590073.480000] usb-storage: device found at 117
[18590073.480000] usb-storage: waiting for device to settle before scanning
[18590078.480000] usb-storage: device scan complete
[18590078.484000]   Vendor:           Model: P990i             Rev: 1.0 
[18590078.484000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[18590078.500000] sd 11:0:0:0: Attached scsi removable disk sdc
[18590078.500000] sd 11:0:0:0: Attached scsi generic sg2 type 0

```

I now see a new icon under "Computer" which looks like a floppy with the USB icon called "P990i"

If I click it I get this error popping up..

```

Unable to mount the selected volume.
mount: no medium found
mount: no medium found
error: could not execute pmount

```

I have formatted my memory stick and I have also tried it with 2 different sticks, the 64 meg san disk that came with it and my brand new 1gig sony card both the same problem.

Oh I am running Edgy Eft too..

elp..

---

### Post by johnwards on 2006-11-25
Anyone?

---

### Post by johnwards on 2006-11-25
Right seems that their is a patch floating around to get this phone working in the linux kernel but I have no idea a)how to find it b) if it will work with the latest Edgy Kernel c) How to patch my current kernel..

Its mentioned here:
[http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.19-rc5](http://www.kernel.org/pub/linux/kernel/v2.6/testing/ChangeLog-2.6.19-rc5)

```

commit 9b823b43ff308c914530ec7fde5e2d79cb37b51a
Author: Jan Mate <mate@fiit.stuba.sk>
Date:   Fri Oct 20 14:51:44 2006 -0700

    USB Storage: unusual_devs.h entry for Sony Ericsson P990i
    
    USB Storage: this patch adds support for Sony Ericsson P990i
    
    Signed-off-by: Jan Mate <mate@fiit.stuba.sk>
    Signed-off-by: Andrew Morton <akpm@osdl.org>
    Signed-off-by: Greg Kroah-Hartman <gregkh@suse.de>

```

Any ideas?

---

### Post by johnwards on 2006-11-27
anyone?

---

### Post by johnwards on 2007-01-08
Try another bump as I don't have access to a windoz machine at the moment to get my photos off the memory card :(

---

### Post by lvanderree on 2007-01-17
Update your phone to the new firmware, that did the trick for me 

(although it also worked with the new kernel in feisty, but I would choose to update your phone, makes it less buggy, which it can use...)

---

### Post by xilix on 2007-01-25
I consider buying the SonyEricsson P990i. Can you tell me WHAT works? 

Is it possible to sync addressbook, tasks, mails, ... with Evolution (via USB/BT) or can you just copy Files on it?

thank you
icicle

---

### Post by lvanderree on 2007-01-25
I will do some testing, and maybe write a short howto later on when I'm back at home.

What I can remember is that you can access the memory stick without a problem over USB.

Bluetooth also works fine for sending files.

Synchronization worked over syncML (via wifi, but probably also possible via bluetooth LAN) for Addressbook, notes, Calendar, but not for TODO. (with the funambol service).
E-mail works via iMAP.

But because I mostly use Opera on my desktop (also for notes and email). I don't sync anymore with my PC. So that's why I don't know it for sure anymore. 

But as I said, I will do some testing when I'm at home again.

---

### Post by xilix on 2007-01-25
That would be awesome.

---

### Post by lvanderree on 2007-01-25
Well did some short testing, little short on time, but here it comes.

did a clean install. Downloaded funambol from:
[http://download.forge.objectweb.org/sync4j/funambol-3.0a.bin](http://download.forge.objectweb.org/sync4j/funambol-3.0a.bin)

installed it using
```
sh funambol-3.0a.bin
```

after this I let the service start.

Checked out if it worked, by using my browser (on my pc) and went to 
```
http://localhost:8080/pimweb
```

But from your phone shoud of course also work by going to ```
http://ip.your.com.puter:8080/pimweb
```

And removed the 3 default contacts and apointments

you can also do this from an application on your computer:
```
cd Funambol/plug-ins/java-gui
./demob.sh
```

then I entered the settings in my phone:
[LIST=1]
[*]Mainmenu
[*]Extra
[*]External Sync
[/LIST]

[LIST=1]
[*]Menu
[*]edit profile
[/LIST]

[LIST]
[*]Profilename: sync-home
[*]ServerAdres: [http://ip.your.com.puter:8080/funambol/ds](http://ip.your.com.puter:8080/funambol/ds)
[*]username: guest
[*]password: guest
[*]transport protocol: http
[*]internetaccount: wifi-home
[/LIST]

Edit sync task for Calendar
[LIST]
[*]Serverdatabase: cal
[/LIST]


Edit sync task for Contacts
[LIST]
[*]Serverdatabase: card
[/LIST]

Synced et voila, all my contacts and appointments are now synced with funambol, and could be seen in the web-app and javaclient.

**Note though that you cannot (yet) have any TODO's, they will make the sync fail (for now...)**

now it should be possible to sync funambol with evolution, with something like:
[http://sourceforge.net/projects/sync4jevolution](http://sourceforge.net/projects/sync4jevolution)

or any other application you want

Maybe it's also possible to sync with multisync, this has a sync-ml server too, but don't have any time to test that now...

---

### Post by xilix on 2007-01-25
Thank you very much. Good to know that it works as a matter of principle.

---

