---
title: "verifying a burnt usb stick against an iso image"
date: 2016-08-14
forum: Hardware
---

### Post by pab10 on 2016-08-14
verifying a burnt usb stick against an iso image

with a dvd/cd burn you can md5sum etc. as it actually is sized (as presented to os) to represent size of iso/img

but usb stick is in volumes plus free space...

so if initialise usb stick to zeroes first should be able to do a verify by appending N 0's to the signature depending on usb stick size?

am I missing something? can you already simply verify usb stick iso burn?

---

### Post by howefield on 2016-08-14
Try this, checked with a Lubuntu 32 bit .iso file that has a sha1sum of... 

```
c0677e79914c9261983633094b3bb7df7e3f1820 *lubuntu-16.04.1-desktop-i386.iso
```

First obtain the size of the .iso file

```
stat -c '%s' lubuntu-16.04.1-desktop-i386.iso
```

then use it to check the USB stick with..

```
sudo head -c 899678208 /dev/sdb | sha1sum
```

eg,

```
hugh@xenial:/Data/Linux/Linux Isos$ stat -c '%s' lubuntu-16.04.1-desktop-i386.iso 
899678208
hugh@xenial:/Data/Linux/Linux Isos$ sudo head -c 899678208 /dev/sdb | sha1sum
[sudo] password for hugh: 
c0677e79914c9261983633094b3bb7df7e3f1820  -
hugh@xenial:/Data/Linux/Linux Isos$
```

---

### Post by pab10 on 2016-08-14
I'll get back to you when I have tested it but I know I am going to already say AWESOME... nice!

**update:**

Yes, Thanks, that works excellently and revealed there were some burn problems as well, though that was not the main problem I was embroiled in...

reckon my problem was not unmount before dd burn and then using sync after burn.

it seems dd flushes it's buffers, so just unmount and dd the image, remove stick... then use your technique to double check! Nice!

---

