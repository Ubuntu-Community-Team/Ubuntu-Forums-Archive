---
title: "Rare AFUDOS bios flasher versions"
date: 2012-08-10
forum: Hardware
---

### Post by nikonian on 2012-08-10
Took ages to find these particular versions of "AFUDOS" DOS BIOS flasher for AMI BIOS, esp Asus mobos.

These versions allow BIOS downgrading...

[http://rapidshare.com/files/4268957509/afudos_207_227.rar](http://rapidshare.com/files/4268957509/afudos_207_227.rar)




You will need to put this on a bootable CD or USB drive along with your BIOS file, as the Bios file is over 2MB and will not fit on a floppy.

Now boot into Dos and type the following,

```
AFUDOS /ixxxxx.ROM /pbnc /n
``` (xxxxx = your bios file name)

example: ```
AFUDOS /iP5KE602.ROM /pbnc /n
```


Make FreeDOS flashdrive for this purpose (tested, not just hearsay):
[http://chtaube.eu/tech/freedos/boot-freedos-from-usb-flash-drive](http://chtaube.eu/tech/freedos/boot-freedos-from-usb-flash-drive)

---

