---
title: "Cannot access to USB or unmount it"
date: 2012-12-30
forum: Hardware
---

### Post by ivotkl on 2012-12-30
Hello. I've seen a few posts about not being able to see USB.

I can also see it on computer and gparted.

lsusb shows me the device:
[code]Bus 001 Device 013: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 102 Flash Drive / HEMA Flash Drive 2 GB / PNY Attache 4GB Stick[/usb]

***However***, I cannot unmount it or access to it. And besides that, it is a 8GB device. Apparently, lsusb recognizes it as a 2 or 4 GB stick (I do not understand what is HEMA or PNY, Google results only taught me that PNY is a memory manufacturer but nothing relevant about HEMA). gparted recognizes it fine (7.46 GiB).

I cannot just go ahead and format it as it was lent to me and has files that do not belong to me. So, I would like to use it after I backup files in it for trying LiveCDs of some linux-based OSs I have downloaded.

BTW, I do not want to install wine or anything related to Bill Gates. =P

Any help would be highly appreciated.

Happy holidays. =)

---

### Post by HomelandSecurity on 2012-12-30
[CODE]
sudo fdisk -l
sudo parted -l

---

### Post by gnush on 2012-12-30
In order to get a list of plugged in disks, execute the following command.

```
sudo fdisk -l
```Once you've done that, it should be fairly easy to identify the memory stick. If you can't identify it, post the output in the thread.

```
sudo mount /dev/sdx ~/dir/usb/
```Use the command *mount* in order to mount the memory stick. Change */dev/sdx *and *~/dir/usb *accordingly.

Then, just enter the directory you specified.

_**Edit:**_

I just noticed you wanted to unmount it. Just use *umount *instead.

```
sudo umount /dev/sdx
```

---

### Post by ivotkl on 2012-12-30
Ok, so I did:

```
sudo mkdir /media/usb
```

And:

```
sudo mount /dev/sdb1 /media/usb/
```

Works great. Thank you and happy new year both of you!

---

