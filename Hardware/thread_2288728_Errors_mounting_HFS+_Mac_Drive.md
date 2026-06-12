---
title: "Errors mounting HFS+ Mac Drive?"
date: 2015-07-29
forum: Hardware
---

### Post by Donnut on 2015-07-29
I am running a triple boot system on my MacBook Air. I have Windows and Ubuntu playing nice together, but Ubuntu refuses to mount my Mac drive. I've installed hfsprogs, and hfsutils. I still get this error. Am I missing something?

Error mounting /dev/sda2 at /media/stephen/e4a9e089-13ce-328a-ba54-3e0ff6274bcc: Command-line `mount -t "hfsplus" -o "uhelper=udisks2,nodev,nosuid" "/dev/sda2" "/media/stephen/e4a9e089-13ce-328a-ba54-3e0ff6274bcc"' exited with non-zero exit status 32: mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by Lars Noodén on 2015-07-29
As it stands you need an extra partition for data between Ubuntu and OS X.  The utilities that  has cannot use a journaled HFS+ partition so you have to make an unjournaled one and you do not want to do that to your main OS X partition.

---

### Post by Donnut on 2015-08-27
Ah. Ok. Thank you. I will just use the NTFS Windows volume as a "go-between".

---

