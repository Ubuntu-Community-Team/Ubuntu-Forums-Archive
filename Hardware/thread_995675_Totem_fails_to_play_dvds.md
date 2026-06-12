---
title: "Totem fails to play dvds"
date: 2008-11-28
forum: Hardware
---

### Post by monster_eater123 on 2008-11-28
I fixed my driver issues with my graphics cards by installing Xubuntu 8.04. But now I cannont play dvds at all Totem gives me this error:

Failed to mount <--MOVIE NAME-->

mount: block device /dev/scd0 is write-protected, mounting read-only
mount: /dev/scd0 already mounted or /media/cdrom0 busy
mount: according to mtab, /dev/scd0 is already mounted on /media/cdrom0.

anybody know whats up?:frown:

---

### Post by cariboo on 2008-11-28
Do you have libdvdcss1 installed? You will have  to enable the Medibuntu repositories in order to install the file. Go here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

and follow the instruction for your particular version. Make sure you scroll down and add the GPG key.

Jim

---

