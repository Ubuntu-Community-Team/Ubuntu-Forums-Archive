---
title: "usb hard drive wont mount"
date: 2009-04-01
forum: Hardware
---

### Post by edzillion on 2009-04-01
As usual I went ahead like a blunderbus and did lots of things I had no idea what I was doing.
Anyway I had a problem accessing the internal drive on my laptop and was getting this error;

Unable to mount device
Error org.freedesktop.Hal.Device.Volume.UnknownFailure

So tried to mount it various ways and then used the bash command:

mount -t ntfs-3g /dev/sda1 /media/sda1 -o force

which worked fine.

Step 2:

Tried to get the USB hard drive to be recognised so I could copy the data off the drive, so again:

mount -t ntfs-3g /dev/sdb /media/sdb -o force

which worked. Copied all the information off the internal drive and then put the usb drive into my windows machine (didnt dismount!). When added it recognises a usb mass storage device but doesnt appear in 'my computer' - no drive letter. Also I tried remounting it but I get the error 'NTFS is either inconsistent, or you have hardware faults......'

any ideas?

---

### Post by edzillion on 2009-04-03
well can anyone help me?

---

