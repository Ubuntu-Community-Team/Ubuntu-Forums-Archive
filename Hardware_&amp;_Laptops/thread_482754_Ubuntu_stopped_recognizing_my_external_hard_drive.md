---
title: "Ubuntu stopped recognizing my external hard drive"
date: 2007-06-24
forum: Hardware &amp; Laptops
---

### Post by potion on 2007-06-24
It was working fine just a few days ago. The only problem was that when I would try to eject it, it wouldn't let me, and I would have to just turn it off or disconnect it in spite of the warnings that I might lose data that way. I would have preferred to eject, of course, but I didn't have that option.

Anyway, it would always recognize the drive fine and automount it. Now, when I connect the drive, it makes this whirring sound, like two whirs a second or so. This just goes on, until I either disconnect the drive or turn it off. But if I disconnect the drive, it goes right back to its normal, healthy-sounding hum. The whir I'm describing is not the sound of a hard drive dying. It sounds like Ubuntu trying to talk to the device and running into the same problem over and over. I don't have another computer on hand to try it with, but I suspect it'll work fine. I'll confirm that tomorrow.

It's a Lacie drive, formatted to ext3. I'm running Feisty (quite happily, I should add). I've never had any problems with the drive until now. I didn't even have to configure it, it was one of the things that worked great out of the box.

Can anyone help? Thanks!

---

### Post by potion on 2007-06-24
Turns out none of the computers I have easy access to have firewire ports! The hard drive is firewire only, so I haven't been able to confirm that it works when connected to other systems. I did try firing up my external DVD drive using firewire, and it works, so the connection's not the issue.

Does anyone have any ideas? Thanks a ton for any help you can give.

---

### Post by elsaturnino on 2007-06-24
You might try running the command after you plug in the drive to see if it is being recognized 

```
dmesg | tail
```

I have a Seagate external hdd (connected through usb) and it has never automounted with Feisty (this is apparently a common problem). Have you always been running Feisty or did you recently upgrade?

---

### Post by potion on 2007-06-24
Thanks for the suggestion, elsaturnino, I really appreciate the help. Here's what came up when I tried that command while the drive was connected and whirring:

```
jon@ubuntu:~$ dmesg | tail
[ 8582.096000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[ 8582.096000] sda: Current: sense key: Medium Error
[ 8582.096000]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 8582.096000] end_request: I/O error, dev sda, sector 0
[ 8582.096000] Buffer I/O error on device sda, logical block 0
[ 8586.004000] sd 0:0:0:0: SCSI error: return code = 0x08000002
[ 8586.004000] sda: Current: sense key: Medium Error
[ 8586.004000]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 8586.004000] end_request: I/O error, dev sda, sector 24
[ 8586.004000] Buffer I/O error on device sda, logical block 3
```

And here's what came up when I tried it again after the disconnecting the drive.

```
jon@ubuntu:~$ dmesg | tail
[ 8609.688000] end_request: I/O error, dev sda, sector 312581800
[ 8609.688000] Buffer I/O error on device sda, logical block 39072725
[ 8609.688000] Buffer I/O error on device sda, logical block 39072725
[ 8609.688000] Buffer I/O error on device sda, logical block 39072725
[ 8609.688000] Buffer I/O error on device sda, logical block 39072725
[ 8609.688000] Buffer I/O error on device sda, logical block 39072718
[ 8609.688000] Buffer I/O error on device sda, logical block 39072724
[ 8609.692000] FAILED
[ 8609.692000]   status = 0, message = 00, host = 1, driver = 00
[ 8609.692000]   
```

I take it from the first output means that Ubuntu's trying to communicate with the drive and not having any luck?

Oh, and I've been using Feisty since soon after it came out. First as an upgrade, later as a reinstall. But it's definitely been some weeks at least since I reinstalled, and I never had any problems...

---

### Post by potion on 2007-06-24
And here's what's in /etc/fstab:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=6626d1d0-703d-479a-8955-a8196432631e /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=6e8c4326-a9b2-43ae-8538-49ffad6bcc0a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

Should there be some mention of the other hard drive? Sorry, I'm still very new to Linux.

---

### Post by potion on 2007-06-24
Very strange... I thought I'd try that dmesg command again to see if anything had changed. So I connected the drive, ran the command, and at first I got this:

```
jon@ubuntu:~$ dmesg | tail
[18937.364000] sd 1:0:0:0: SCSI error: return code = 0x08000002
[18937.364000] sda: Current: sense key: Medium Error
[18937.364000]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
[18937.364000] end_request: I/O error, dev sda, sector 0
[18937.364000] Buffer I/O error on device sda, logical block 0
[18941.424000] sd 1:0:0:0: SCSI error: return code = 0x08000002
[18941.424000] sda: Current: sense key: Medium Error
[18941.424000]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
[18941.424000] end_request: I/O error, dev sda, sector 24
[18941.424000] Buffer I/O error on device sda, logical block 3
```

But then I noticed it had stopped whirring, so I tried again:

```
jon@ubuntu:~$ dmesg | tail
[18945.372000] end_request: I/O error, dev sda, sector 24
[18945.372000] Buffer I/O error on device sda, logical block 3
[18949.380000] sd 1:0:0:0: SCSI error: return code = 0x08000002
[18949.380000] sda: Current: sense key: Medium Error
[18949.380000]     Additional sense: Logical unit communication CRC error (Ultra-DMA/32)
[18949.380000] end_request: I/O error, dev sda, sector 0
[18949.380000] Buffer I/O error on device sda, logical block 0
[18949.380000]  unknown partition table
[18949.380000] sd 1:0:0:0: Attached scsi disk sda
[18949.380000] sd 1:0:0:0: Attached scsi generic sg0 type 14
```

I figured at least it's saying something's attached now. Apart from that, I can't tell what anything means. But then now it says...

```
[19511.940000] sdb: Write Protect is off
[19511.940000] sdb: Mode Sense: 6c 00 00 08
[19511.940000] sdb: assuming drive cache: write through
[19511.944000] SCSI device sdb: 58605120 512-byte hdwr sectors (30006 MB)
[19511.944000] sdb: Write Protect is off
[19511.944000] sdb: Mode Sense: 6c 00 00 08
[19511.944000] sdb: assuming drive cache: write through
[19511.944000]  sdb: sdb1 sdb2
[19511.956000] sd 2:0:0:0: Attached scsi removable disk sdb
[19511.956000] sd 2:0:0:0: Attached scsi generic sg1 type 0
```

No mention of any errors at all, and the disk is humming, not whirring... But I still can't see it anywhere. I'm now searching for what to do in this situation, but if anyone happens to see this and can point me in the right direction, I'd be grateful!

---

### Post by potion on 2007-06-24
Well, decided to restart with the drive on and connected, since it seemed to be recognized now, and it worked! I can't imagine what changed between when it wasn't working and now, but I'm happy it's back...

Also means I can stop the running commentary. Thanks very much for the help, elsaturnino.

---

### Post by elsaturnino on 2007-06-25
The buffer I/O errors are a bit disconcerting but at least it is working now :) Ubuntu seems to be having quite a few problems with external hard drives these days. To be safe, you might want to try it the drive on another firewire-enabled computer to see if it is actually a problem with the hard drive itself. Hopefully they will get this sort of thing worked out in the future. Best of luck with Ubuntu.

---

### Post by kamiccolo291 on 2007-07-02
I was having the same problem, where I couldn't get Ubuntu to find a external hard drive that had worked fine in the past.

For those of you who this post didn't help, look at the back of the machine and make sure you didn't blindly plug the USB cable into your ethernet port...

---

