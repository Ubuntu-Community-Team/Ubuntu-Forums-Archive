---
title: "eject usb storage device fails ?"
date: 2006-07-03
forum: Hardware &amp; Laptops
---

### Post by madmack on 2006-07-03
Hello everybody, i'm fairly new to linux. so bare with me
I have a Nokia N80 phone that is supposed to work as a USB storage device when connected. First, it didn't work, i had to compile a new kernel and patch it. It did work after compilation, (i.e. i can read/write to it) but i couldn't successfuly "eject" the phone. here is what happens when i use the eject command:

```

user@ubuntu:/media$ sudo eject -vs sda
eject: device name is `sda'
eject: expanded name is `/dev/sda'
eject: `/dev/sda' is not mounted
eject: `/dev/sda' is not a mount point
eject: `/dev/sda' is a multipartition device
eject: unmounting `/dev/sda1'
eject: trying to eject `/dev/sda' using SCSI commands
eject: SCSI eject succeeded

```

Well, it says succeeded, but on the phone, it keeps saying "Data transfering mode, do not unplug" or something similar. and when i just unplug the cable, the phone tells me something about losing data this way and that i should "safely remove hardware". Is the eject command really working ? is there any way to force an eject, sort of kill all power/data supplied to this usb device ?
I booted into my windows partition to see what's the normal behavior of the phone upon using the "safely remove hardware" command, the phone actually responded by saying "it is now safe to unplug the USB cable", and that's the message i'm hoping to get with Ubuntu.
any help would be appreciated.

---

### Post by wildekek on 2006-07-05
I have exactly the same problem here, but then using a usb harddrive i'd like to 'eject' as you call it. I've been looking in the forums and on the interweb, but to no avail. What you mean by ejecting is pbb switching the usb connection off. This is not really necessary with a usb device under normal circumstances, 'cause the scsi eject command will sync (and spool down when it's a harddisk). When the disk is removed from USB it also unmounts automaggically, so nobody is really interested in this feature.
You are, because you don't like the message your phone gives you (which is nothing to really worry about imho, since it is already synced by the scsi command). I'm interrested in the command because i'd like my usb hdd light to switch off, so people can see the drive has finished it's backup procedure.
Anyway, the only solution i can think of is switching the whole usb port off, but how we could manage that? Not a clue.

---

### Post by madmack on 2006-07-05
Hey, thanks for the reply. I guess i will start ignoring this warning that i receive from my cell. I wasn't sure of whether i should remove the usb cable or not, but now i will. But if anybody knows of a way to turn the whole USB port off, by perhaps rmmod something, I'd be more than glad to know it.

---

### Post by wildekek on 2006-07-06
I tried to rmmod al usb modules, but that doesn't switch the usb port off.

---

