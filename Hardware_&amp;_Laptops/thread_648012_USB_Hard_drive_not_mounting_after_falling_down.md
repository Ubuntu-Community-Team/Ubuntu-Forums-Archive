---
title: "USB Hard drive not mounting after falling down"
date: 2007-12-23
forum: Hardware &amp; Laptops
---

### Post by nair.arun on 2007-12-23
Hey Guys,

My external hard drive fell down and since then doesn't mounts when i give the command 
dmesg it says: 
[ 4925.752000] usb 5-3: new high speed USB device using ehci_hcd and address 7
[ 4925.884000] usb 5-3: configuration #1 chosen from 1 choice
[ 4925.884000] scsi5 : SCSI emulation for USB Mass Storage devices
[ 4925.884000] usb-storage: device found at 7
[ 4925.884000] usb-storage: waiting for device to settle before scanning
[ 4930.884000] usb-storage: device scan complete
[ 4936.664000] usb 5-3: USB disconnect, address 7
[ 4936.664000] scsi 5:0:0:0: scsi: Device offlined - not ready after error recovery

Kindly help me out with this this problem I'm stuck with all my university data in it and am unable to get access to it.

Thanks in advance and the help is very much appreciated.

Regards,

Arun Nair

---

### Post by Ehtetur on 2007-12-23
Maybe the sata or ide drive came loose.
Try opening the case and reseat the drive.

Good luck!

---

### Post by nair.arun on 2007-12-24
Isn't there any other way out apart from opening the drive

---

### Post by nickg on 2007-12-24
I think that Ehtetur meant check that the cabling between the drive and the motherboard is not loose - not for you to take the hard drive apart. There are very few things that you can fix yourself on a hard drive unfortunately. If the fault is not as simple as a displaced connector cable / faulty driver hardware on the motherboard then it is a difficult job to get the data off the hard drive. There are some data recovery companies that can do this for you, but they can be expensive. Might be worth trying unplugging the drive from your machine and fitting it into another machine entirely as a second drive and seeing if you can read it and back it up.

---

### Post by nair.arun on 2007-12-24
Sorry mate already tried that n number of times but the thing was the hard disk fell off its leather pouch by its corner on the wooden table

---

### Post by nickg on 2007-12-24
Give some of the hard drive / data recovery tools from [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) a try such as HDAT2 (which is supposed to support USB drives - big caveat I haven't tried it, but the software on the UBCD website has a good reputation)?

---

### Post by nair.arun on 2007-12-25
Sorry doesn't works with the ultimate boot cd as a matter of fact when I try to set the boot from device with other usb it shows the option of booting from the usb but not with the problematic one it doesnt gets detected at the low level bios but when i give the dmesg i get the same message described above

please help and all help is appreciated

Arun

---

### Post by nickg on 2007-12-27
OK, lets start at the begining with a question I should have asked first: what type of drive is it (manufacturer and model number)? And what types of partitions do you have on it? Not sure that there is a lot that can be done, but knowing something of the electrical / mechanical systems that you actually have in front of you might help.

---

### Post by mamlouk on 2007-12-27
My best bet is that you have already lost your hard-drive, including data. You will probably notice that the drive's LED is flashing continuously, while your linux log will tell you that the drive is trying to reset. This is probably because the drive heads cannot access track 0 which, in a way, initiates your drive to be detected on any OS. The data recovery tools that I know of work on already-detected drives. That is, your drive is detected, but you can see it as unformated, or empty. If your drive cannot be initiated, then none of these tools will work, since linux is unable to assign a /dev folder to it.

I hate to be the bearer of bad news, but maybe someone else has a way to re-allign the heads or something, but I doubt it.

---

