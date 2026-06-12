---
title: "Can't create/move files to fat32 usb drive"
date: 2007-06-16
forum: Hardware &amp; Laptops
---

### Post by Scooter7 on 2007-06-16
[COLOR="Red"][STATUS: SOLVED][/COLOR]

Hi, I need to move some files from my Ubuntu 7.04 server to my USB external hard drive, which is formatted to fat32.

The thing is, if I try copying a file onto it, I'm told that I don't have the correct permissions.

I ran this command to try and correct that:

```
sudo chown scooter7 LACIE
``` (that being run from /media)

I'm then told that the filesystem is 'read-only'.

I tried mounting the drive as read-write, among other things, using the fat guides here: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Windows)

Does anyone know what I can do?

Thanks,

   ~Vertimyst (scooter7, teh ds)

---

### Post by Scooter7 on 2007-06-16
*bump*

...also, I'm currently repartitioning the drive to be ext3.   Hopefully that will clear things up.

-UPDATE-

I've successfully repartitioned it, and it's working.

...looks like just posting here helps me solve problems. :P

   ~Vertimyst

---

