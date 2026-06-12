---
title: "motorola v8"
date: 2007-09-23
forum: Hardware &amp; Laptops
---

### Post by biji on 2007-09-23
hi all,

i have problem connecting motorola razr2 v8 as memory device :(
linux detect it as /dev/sg0 
not sda or sda1

i don't know it should be standard usb storage
please help..
thanks

---

### Post by wallyhall on 2007-09-23
See:

[http://www.redhat.com/archives/rhl-list/2004-May/msg01725.html](http://www.redhat.com/archives/rhl-list/2004-May/msg01725.html)

Apparently (I just googled for "/dev/sg0") sg devices a anything which isn't a SCSI scanner, block device (HDs, CDRoms etc) or tape.  Motorola phones are known to be very "weird" (they use propriety "usb" connectors), it's just a guess but I imagine the phone needs special drivers from Motorola, which will naturally only be available for Windows.

There might be some Linux drivers for copying files up and down, but otherwise you're stuffed.  The phone isn't a USB mass storage device, it's a "special" device.

If there's anything I can do for you, let me know.

My next step I were you would to be either buy a new phone (joking! motorolas are great) or try getting a cheap Linux compatible bluetooth dongle.  I've had a lot of success with my cheapo L6 and bluetooth on Linux.

---

### Post by R.Bucky on 2007-09-23
> **wallyhall said:**
> See:

[http://www.redhat.com/archives/rhl-list/2004-May/msg01725.html](http://www.redhat.com/archives/rhl-list/2004-May/msg01725.html)

Apparently (I just googled for "/dev/sg0") sg devices a anything which isn't a SCSI scanner, block device (HDs, CDRoms etc) or tape.  Motorola phones are known to be very "weird" (they use propriety "usb" connectors), it's just a guess but I imagine the phone needs special drivers from Motorola, which will naturally only be available for Windows.

There might be some Linux drivers for copying files up and down, but otherwise you're stuffed.  The phone isn't a USB mass storage device, it's a "special" device.

If there's anything I can do for you, let me know.

My next step I were you would to be either buy a new phone (joking! motorolas are great) or try getting a cheap Linux compatible bluetooth dongle.  I've had a lot of success with my cheapo L6 and bluetooth on Linux.

Try ```
sudo apt-get install moto4linux
```
This program has had some success with the Motorolla product line.

---

### Post by biji on 2007-09-23
Hi found some information here but for motorola z6:

[http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg19221.html](http://www.mail-archive.com/linux-usb-users@lists.sourceforge.net/msg19221.html)

I'm sure it is just regular usb storage because dmesg says scanning partition which failed and turn into sg0

---

### Post by biji on 2007-09-23
> **wallyhall said:**
> See:

[http://www.redhat.com/archives/rhl-list/2004-May/msg01725.html](http://www.redhat.com/archives/rhl-list/2004-May/msg01725.html)
 Motorola phones are known to be very "weird" (they use propriety "usb" connectors), it's just a guess but I imagine the phone needs special drivers from Motorola, which will naturally only be available for Windows.


nope it is standard... called micro USB, there's also mini USB, etc.
see wikipedia ^^

---

### Post by dysphasi on 2007-11-02
Hey all, I've got this phone and after playing about with all sorts of players etc..  with supposed MTP device support  to get access to this device from ubuntu.

I think I've found a satisfactory solution as follows:

1) From the terminal type:
```
sudo aptitude install libfuse-dev libmad0-dev
```

2) Download MTPFS from here: [http://www.adebenham.com/debian/mtpfs_0.7-1_i386.deb](http://www.adebenham.com/debian/mtpfs_0.7-1_i386.deb)

3) Install it from the deb

4) Create a folder in your home directory, eg. MTPdevice

5) Add yourself to the "fuse" group: System > Administration > Users and Groups > Manage Groups > fuse > properties and then your username. Logout and login.

6) On your motorola go to Main menu > Settings > Connections > USB Setting and set this to 'Media Sync.'

7) Plug in and from the terminal type:
```
mtpfs ~/MTPdevice
```

You should now be able to access the phone via this folder and drag/drop music etc.. as you like.

ps...I found most of this from: [http://ubuntuforums.org/showthread.php?p=2397682](http://ubuntuforums.org/showthread.php?p=2397682)

8) Finally, when you're done, you can unmount from the terminal as follows:
```
fusermount -u ~/MTPdevice
```

Hope this is of some help, if anyone makes any better progress please let me know

---

### Post by andreimatei on 2007-11-09
Thanks dysphasi, that worked for me. But only for copying music, not for photos. The photos dir appears empty. It's the same in Windows, except that in Windows I can set the "USB connection type" of the phone to memory device instead of media player, and then when I connect it I see a slightly different directory structure, which includes the photos. In Linux, when I switch to memory device and plug it in, nothing happens. Any ideeas why? Shouldn't it behave like a usb memory stick?

---

### Post by dysphasi on 2007-11-09
Don't know if it is of any help, but F-Spot Photo Manager should let you import any photos from the phone as long as it's set up as above in 'Media Sync' mode.

Afraid I don't know enough about the workings of all these things to offer a real solution so I'll leave it open to 'the panel' as it were.

---

### Post by andreimatei on 2007-11-09
Here's what dmesg shows after I plug in the phone, set to "Memory device" usb connection mode.

[11947.876000] usb 5-3: new high speed USB device using ehci_hcd and address 4
[11948.012000] usb 5-3: configuration #1 chosen from 1 choice
[11948.232000] usbcore: registered new interface driver libusual
[11948.300000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[11948.300000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[11948.316000] Initializing USB Mass Storage driver...
[11948.316000] scsi2 : SCSI emulation for USB Mass Storage devices
[11948.316000] usb-storage: device found at 4
[11948.316000] usb-storage: waiting for device to settle before scanning
[11948.316000] usbcore: registered new interface driver usb-storage
[11948.316000] USB Mass Storage support registered.
[11953.316000] usb-storage: device scan complete
[11953.316000] scsi 2:0:0:0: Direct-Access     Motorola MSnc.                 PQ: 1 ANSI: 4 CCS
[11953.316000] scsi 2:0:0:0: Attached scsi generic sg2 type 0


Any ideeas about how I can mount or use it?

---

### Post by andreimatei on 2007-11-09
And if I try to mount it...

andrei@andrei-mb:/mnt$ sudo mount /dev/sg2 /mnt/sg2/
[sudo] password for andrei:
mount: /dev/sg2 is not a block device

---

### Post by Supersaiyan.IV on 2007-11-11
> **andreimatei said:**
> And if I try to mount it...

andrei@andrei-mb:/mnt$ sudo mount /dev/sg2 /mnt/sg2/
[sudo] password for andrei:
mount: /dev/sg2 is not a block device

Try setting your V8 to Modem connection, set ACM device to: /dev/ttyACM0
And update the usb device numbers below.

[device]
cfgACMdevice=/dev/ttyACM0
**cfgATproduct=6422**
cfgATvendor=22b8
cfgAutoConnect=1
cfgDetachDriver=0
**cfgP2Kproduct=6424**
cfgP2Kvendor=22b8

[filemanager]
cfgAutoExpandDirTree=0
cfgAutoUpdateFileList=1
cfgGoLastFolder=0
cfgLoadList=0


Note the difference between p2k and AT.
If it still doesn't work, read this thread and find out why:

[http://www.modmymoto.com/forums/showthread.php?t=55391]("http://www.modmymoto.com/forums/showthread.php?t=55391")

Motorola V8 is simply not yet p2k enabled.

---

