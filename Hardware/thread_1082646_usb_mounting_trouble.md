---
title: "usb mounting trouble"
date: 2009-02-28
forum: Hardware
---

### Post by nwadams on 2009-02-28
I'm having problems getting usb sticks and my usb external hdd to auto mount. 

when i try to mount it with the gui or plug it in it gives me this error

Invalid mount option when attempting to mount the volume.

the following gives
sudo mount /dev/sdb1  

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I can force mount it and it works but i want it to auto mount. 

Thanks for any help you can provide.

---

### Post by ProNux on 2009-02-28
> **nwadams said:**
> I'm having problems getting usb sticks and my usb external hdd to auto mount. 

when i try to mount it with the gui or plug it in it gives me this error

Invalid mount option when attempting to mount the volume.

the following gives
sudo mount /dev/sdb1  

mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

I can force mount it and it works but i want it to auto mount. 

Thanks for any help you can provide.

Is this a newly-installed Ubuntu?  Or before it worked well and all of a sudden it turned out that way?

I am asking this because I got the same problem after installing using live USB (NOT LIVE CD).  I used a Live USB thinking it would be faster to install.  After installing, I was greeted with that similar error.

And besides that error, the system found a USB CDROM mounted which I DO NOT HAVE.  I thik inmy case, that was related to the installation using Live USB. 

So what I did was simply reinstalled using Live CD and got it solved.

---

### Post by nwadams on 2009-02-28
ya, it worked for a while. And yes I used a live usb.
i don't want to re-install unless i absolutly have to

---

### Post by zander1013 on 2009-02-28
perhaps a reformat of the usb drive?

---

### Post by nwadams on 2009-02-28
i could, but i'd rather not have to backup and format my terabyte external hdd.

---

### Post by albinootje on 2009-02-28
> **nwadams said:**
> i could, but i'd rather not have to backup and format my terabyte external hdd.

Do you have /dev/sdb1 already defined in /etc/fstab ?
Please post the output of :
```

dmesg|grep sdb
cat /etc/fstab
mount

```

---

