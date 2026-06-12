---
title: "Sony Ericsson W800 Mobile Phone Issues"
date: 2008-11-25
forum: Hardware
---

### Post by EmyrB on 2008-11-25
Hi All,

I have the above phone and before Intrepid, when ever I plugged in the device it would mount as a USB device so I could get at my pictures (it has a built in camera) and import and export MP3 tracks.

Now under Intrepid, it does not mount as a USB device, but the new "improved" Netwrok Manager Applet keeps popping up every 30 seconds saying a new mobile internet device has been found. :mad:

My question is how do I get network manager to stop popping up every 30 seconds (and this is not an exaggeration, I did time it)? And also how do I get Intrepid to auto mount this as a USB device as it did before?

I really don't want to dual boot this box just so I can access a device I used to be able to access under previous versions of Ubuntu. :mad:

Cheers

EmyrB

---

### Post by tgalati4 on 2008-11-25
After plugging in the phone, post the output of:

>dmesg | tail -n 30

Under Gutsy with a Sony-Ericsson w810i, my dmesg looks like:

[ 7018.779843] usb 3-2: new full speed USB device using uhci_hcd and address 2
[ 7019.014625] usb 3-2: configuration #1 chosen from 1 choice
[ 7019.079641] cdc_acm 3-2:1.1: ttyACM0: USB ACM device
[ 7019.082823] cdc_acm 3-2:1.3: ttyACM1: USB ACM device
[ 7019.084706] usbcore: registered new interface driver cdc_acm
[ 7019.084815] /build/buildd/linux-source-2.6.22-2.6.22/drivers/usb/class/cdc-acm.c: v0.25:USB Abstract Control Model driver for USB modems and ISDN adapters
[ 7028.846046] usb 3-2: USB disconnect, address 2
[ 7034.158744] usb 3-2: new full speed USB device using uhci_hcd and address 3
[ 7034.335608] usb 3-2: configuration #1 chosen from 1 choice
[ 7034.338611] scsi3 : SCSI emulation for USB Mass Storage devices
[ 7034.338671] usb-storage: device found at 3
[ 7034.338673] usb-storage: waiting for device to settle before scanning
[ 7034.341725] scsi4 : SCSI emulation for USB Mass Storage devices
[ 7034.341784] usb-storage: device found at 3
[ 7034.341786] usb-storage: waiting for device to settle before scanning
[ 7039.332735] usb-storage: device scan complete
[ 7039.332819] usb-storage: device scan complete
[ 7039.335775] scsi 3:0:0:0: Direct-Access     SEMC     Int.Memory       0000 PQ: 0 ANSI: 0
[ 7039.335817] scsi 4:0:0:0: Direct-Access     SEMC     Mem-Stick        0000 PQ: 0 ANSI: 0
[ 7039.346698] sd 3:0:0:0: [sdd] 54008 512-byte hardware sectors (28 MB)
[ 7039.351690] sd 3:0:0:0: [sdd] Write Protect is off
[ 7039.351694] sd 3:0:0:0: [sdd] Mode Sense: 00 6a 00 00
[ 7039.351696] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[ 7039.360678] sd 3:0:0:0: [sdd] 54008 512-byte hardware sectors (28 MB)
[ 7039.365672] sd 3:0:0:0: [sdd] Write Protect is off
[ 7039.365676] sd 3:0:0:0: [sdd] Mode Sense: 00 6a 00 00
[ 7039.365678] sd 3:0:0:0: [sdd] Assuming drive cache: write through
[ 7039.365682]  sdd: sdd1
[ 7039.378692] sd 3:0:0:0: [sdd] Attached SCSI removable disk
[ 7039.378741] sd 3:0:0:0: Attached scsi generic sg4 type 0
[ 7039.388640] sd 4:0:0:0: [sde] 7999298 512-byte hardware sectors (4096 MB)
[ 7039.393631] sd 4:0:0:0: [sde] Write Protect is off
[ 7039.393637] sd 4:0:0:0: [sde] Mode Sense: 00 6a 00 00
[ 7039.393643] sd 4:0:0:0: [sde] Assuming drive cache: write through
[ 7039.402621] sd 4:0:0:0: [sde] 7999298 512-byte hardware sectors (4096 MB)
[ 7039.408616] sd 4:0:0:0: [sde] Write Protect is off
[ 7039.408623] sd 4:0:0:0: [sde] Mode Sense: 00 6a 00 00
[ 7039.408629] sd 4:0:0:0: [sde] Assuming drive cache: write through
[ 7039.408633]  sde: sde1
[ 7039.422612]  sde: p1 exceeds device capacity
[ 7039.424631] sd 4:0:0:0: [sde] Attached SCSI removable disk
[ 7039.424683] sd 4:0:0:0: Attached scsi generic sg5 type 0
[ 7040.024511] attempt to access beyond end of device
[ 7040.024519] sde: rw=0, want=7999300, limit=7999298
[ 7040.024523] Buffer I/O error on device sde1, logical block 3999554
[ 7040.025144] attempt to access beyond end of device
[ 7040.025149] sde: rw=0, want=7999302, limit=7999298

---

### Post by EmyrB on 2008-11-26
> **tgalati4 said:**
> After plugging in the phone, post the output of:

>dmesg | tail -n 30


Sure thing, I will do this as soon as I get home tonight :)

---

### Post by EmyrB on 2008-11-26
As promised, here is the output of dmesg | tail -n 30

[  156.437613] ppdev0: registered pardevice
[  156.484835] ppdev0: unregistered pardevice
[  156.545607] ppdev0: registered pardevice
[  156.592639] ppdev0: unregistered pardevice
[47350.064535] usb 2-2: new full speed USB device using ohci_hcd and address 4
[47350.241200] usb 2-2: configuration #1 chosen from 1 choice
[47350.651318] cdc_acm 2-2:1.1: ttyACM0: USB ACM device
[47350.654952] cdc_acm 2-2:1.3: ttyACM1: USB ACM device
[47350.658848] usbcore: registered new interface driver cdc_acm
[47350.660558] cdc_acm: v0.26:USB Abstract Control Model driver for USB modems and ISDN adapters
[47350.673665] usbcore: registered new interface driver libusual
[47350.737562] Initializing USB Mass Storage driver...
[47350.741793] scsi6 : SCSI emulation for USB Mass Storage devices
[47350.743804] usbcore: registered new interface driver usb-storage
[47350.743816] USB Mass Storage support registered.
[47350.751018] usb-storage: device found at 4
[47350.751036] usb-storage: waiting for device to settle before scanning
[47355.749184] usb-storage: device scan complete
[47355.760164] scsi 6:0:0:0: Direct-Access     Sony Eri Memory Stick     0000 PQ: 0 ANSI: 0
[47355.815845] sd 6:0:0:0: [sdc] 3926016 512-byte hardware sectors (2010 MB)
[47355.825250] sd 6:0:0:0: [sdc] Write Protect is off
[47355.825271] sd 6:0:0:0: [sdc] Mode Sense: 00 6a 00 00
[47355.825276] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[47355.843475] sd 6:0:0:0: [sdc] 3926016 512-byte hardware sectors (2010 MB)
[47355.856795] sd 6:0:0:0: [sdc] Write Protect is off
[47355.856824] sd 6:0:0:0: [sdc] Mode Sense: 00 6a 00 00
[47355.856830] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[47355.856845]  sdc: sdc1
[47355.880612] sd 6:0:0:0: [sdc] Attached SCSI removable disk
[47355.880875] sd 6:0:0:0: Attached scsi generic sg4 type 0

---

### Post by EmyrB on 2008-11-26
I also noticed that under removable devices when I have the Sony Ericsson plugged in with the Network Manager flashing away every 30 seconds that I have an entry called: - Memory StickDrive. If I try to access it, I get the following error message: -

```
Cannot invoke CheckForMedia on HAL: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
```

Maybe this will help.

---

### Post by EmyrB on 2008-11-28
Any ideas folks as this is bugging me as it used to work flawlessly with Ubuntu for the last 3 years?

Cheers

EmyrB

---

### Post by HungryMan on 2008-12-14
I too am having issues with my w800i.

XS++ fails to connect, the phone just charges when I plug it to my computer, and dmesg's output is kind of disturbing.

But I *think* the phone's hardware just failed. It's a pretty old phone that was handed down to me anyway. Even the joystick is so unresponsive!

---

### Post by EmyrB on 2008-12-17
Has this baffled the mighty Ubuntu Forum Members? Surely not ;)

Seriously, I would still like to solve this issue, but as I needed the piccies on it pronto I went and dual booted the PC in question with Windows XP which is far from an ideal situation as I have been Windows free for over 3 years (and unlike Berenger, I want to stay with Linux and move away from Mickeysoft, especially in light of the recent IE7 flaw).

Cheers

EmyrB

---

### Post by nostrand on 2009-01-02
I have the same problem =/

---

### Post by stedevil on 2009-08-12
> **EmyrB said:**
> Now under Intrepid, it does not mount as a USB device, but the new "improved" Netwrok Manager Applet keeps popping up every 30 seconds saying a new mobile internet device has been found. :mad:


Having the same problem with a W800 under 9.04 jaunty. (Actually I get "network disconnected" every 30s, but surely the same problem).

It must be the countermeasure for "usb-modems-that-start-as-storagedevices-with-windows-drivers" and make them work under Linux automagically that screws things up.

I guess what would really be needed here is a way to manually decide what should be done to a device when it's connected. Ie a popup with the following

Connect USB device as:
( ) Modem
( ) Mass storage device

[ ] Always do selected in the future

---

### Post by tgalati4 on 2009-08-12
Under Jaunty, my w810i popped up as 3 differnt windows:  Create a Network--cancel, Photos--Open with, Music--Open with.

So perhaps there is some breakage with device selection.

---

### Post by TariBuntu on 2009-10-20
Hello people,

I'm having the same problem here since 8.10.
I used to keep a copy of 8.04 on a different partition where it used to work with no problems, but that's no real solution. I've googled my head off, but nothing.

Hope somebody smart pops up with a solution. I have no plans (nor means or real need) to get a new phone, and I have no intention of going to windoze to copy my files.

Sigh...

---

### Post by Zteam on 2010-01-10
A easy workaround if to make this behavior go away is to just choose some random operator and settings, and then it shouldn't ask you anymore, works perfectly for me anyway ;)

---

