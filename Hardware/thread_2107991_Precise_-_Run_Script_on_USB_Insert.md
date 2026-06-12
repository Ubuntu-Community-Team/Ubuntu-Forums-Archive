---
title: "Precise - Run Script on USB Insert"
date: 2013-01-23
forum: Hardware
---

### Post by mastermindg on 2013-01-23
I have a Samsung Galaxy S3 that I'd like to automatically mount when it is inserted. I'm using go-mtpfs to mount the phone's filesystems to a directory and this is working great for me.

I created a UDev rule (51-android.rules):

```
ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="04e8", SYSFS{idProduct}=="6860", RUN+="mounts3"

```
for my device:

```
Bus 001 Device 012: ID 04e8:6860 Samsung Electronics Co., Ltd GT-I9100 Phone [Galaxy S II]
  idVendor           0x04e8 Samsung Electronics Co., Ltd

```

mounts3:

```
go-mtpfs /home/me/MyAndroid
```

However, mounts3 is not running when my device is inserted. Help, please :)

---

### Post by mastermindg on 2013-01-23
Using the following guide I was able to successfully setup udev to mount/automount my S3:

[http://bernaerts.dyndns.org/linux/247-ubuntu-automount-nexus7-mtp](http://bernaerts.dyndns.org/linux/247-ubuntu-automount-nexus7-mtp)

```
# Samsung Galaxy S3 MTP mode : automatic mount when plugged
ENV{ID_MODEL}=="SAMSUNG_Android_SGH-T999", ENV{ID_MODEL_ID}=="6860", ACTION=="add", RUN+="/usr/bin/sudo -b -u ken /usr/bin/go-mtpfs -allow-other=true /home/me/MyAndroid"

# Samsung Galaxy S3 MTP mode : automatic unmount when unplugged
ENV{ID_MODEL}=="SAMSUNG_Android_SGH-T999", ENV{ID_MODEL_ID}=="6860", ACTION=="remove", RUN+="/bin/umount /home/me/MyAndroid"
```

---

### Post by linfidel on 2013-02-10
> **mastermindg said:**
> Using the following guide I was able to successfully setup udev to mount/automount my S3:

[http://bernaerts.dyndns.org/linux/247-ubuntu-automount-nexus7-mtp](http://bernaerts.dyndns.org/linux/247-ubuntu-automount-nexus7-mtp)

```
# Samsung Galaxy S3 MTP mode : automatic mount when plugged
ENV{ID_MODEL}=="SAMSUNG_Android_SGH-T999", ENV{ID_MODEL_ID}=="6860", ACTION=="add", RUN+="/usr/bin/sudo -b -u ken /usr/bin/go-mtpfs -allow-other=true /home/me/MyAndroid"

# Samsung Galaxy S3 MTP mode : automatic unmount when unplugged
ENV{ID_MODEL}=="SAMSUNG_Android_SGH-T999", ENV{ID_MODEL_ID}=="6860", ACTION=="remove", RUN+="/bin/umount /home/me/MyAndroid"
```
Thanks for following up.  I've been trying to get my Samsung Galaxy tab 2 (tablet) with Jelly Bean to mount using that, and it doesn't work at all.  Are you using 32-bit or 64-bit.  It seems like I've had problems since moving from 32 to 64 bit Ubuntu 12.04.1; it works, but has problems like causing Nautilus to lock up for a while periodically.

I also don't understand the sudo for the mount command - does it prompt you for the password?  I would think that it's not really needed to mount in your home directory anyway, just in /media.  I know I don't need sudo to run go-mtpfs on the command line.

---

