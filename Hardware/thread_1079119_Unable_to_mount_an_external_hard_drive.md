---
title: "Unable to mount an external hard drive"
date: 2009-02-24
forum: Hardware
---

### Post by Souljah on 2009-02-24
Hi,

I'm using Hardy Heron 8.04. I have a problem mounting an external hard drive. It's 250gb in size. It's viewable in windows xp but I can't see the contents in Ubuntu. It gives me an error message. I have two options appears in the places menu. One says '250gb External HDD' which is the name I gave to the drive, and the other says '110.6 GB Media' which I can open but inside it has a lost and found folder which I cannot view. Bear in mind, I haven't used the whole hard drive, only a portion of it. The error I am getting is attached with an image. I tried to follow the directions and force the mount but it doesn't seem to be working. How can I get it to work?

Ryan

---

### Post by ChibiLink16 on 2009-02-24
do you have all the correct drivers installed? try googling the HDD model for the download links for drivers.

---

### Post by Souljah on 2009-02-24
I don't understand. Why would I need drivers? I apologize for the blunt remark but the only reason I say that is because before I had formatted the whole drive into NTFS and it mounted perfectly fine, without any need of a driver. I was using the whole drive space.

---

### Post by prshah on 2009-02-24
> **ChibiLink16 said:**
> do you have all the correct drivers installed? try googling the HDD model for the download links for drivers.

Sorry, but that is just plain crap.

> **Souljah said:**
> I have a problem mounting an external hard drive

The hard drive is not automounting because when you were using it in Windows, you have probably :

a) Either not shutdown Windows properly ==or==
b) Removed the hard drive without using the "Safely Remove Hardware" method.

In either case, the HDD is marked as "dirty". The resolution is mentioned in the error message; the easiest is to boot up in Windows, run chkdsk on the drive, then use "Safely Remove Hardware" to remove the drive.

Alternately you can "force" mount it in Ubuntu as per the instructions mentioned.

---

### Post by Souljah on 2009-02-24
> **prshah said:**
> Sorry, but that is just plain crap.



The hard drive is not automounting because when you were using it in Windows, you have probably :

a) Either not shutdown Windows properly ==or==
b) Removed the hard drive without using the "Safely Remove Hardware" method.

In either case, the HDD is marked as "dirty". The resolution is mentioned in the error message; the easiest is to boot up in Windows, run chkdsk on the drive, then use "Safely Remove Hardware" to remove the drive.

Alternately you can "force" mount it in Ubuntu as per the instructions mentioned.

Which I have done. I haven't gone into windows and tried to safely remove the drive, but it doesn't matter now, I'm just going to format it again. I backed up the data. I have to work today so no time to do any of that stuff :P

---

