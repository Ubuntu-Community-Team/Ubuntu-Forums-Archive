---
title: "Install linux for dual boot"
date: 2009-03-13
forum: Installation &amp; Upgrades
---

### Post by 0ra1suicid3 on 2009-03-13
first i installed refit, then instaled linux then i rebooted with refit  but when i select the linux partition  it gives me this:

using load option "usb" error:not found returned from legacy loader

then it gives me this ward message that the firmware refused to boot partition and that it  dosent support external hd  is supported by apple 

in mac, i type ```
diskutil list 
``` 

```
drmons0501w-142177079108:~ simontremblay$ diskutil list
/dev/disk0
   #:                       TYPE NAME                    SIZE       IDENTIFIER
   0:      GUID_partition_scheme     *698.6 Gi         disk0
   1:                        EFI                         200.0 Mi         disk0s1
   2:     Apple_HFS Simon HD            425.4 Gi         disk0s2
   3:                        EFI                         272.9 Gi         disk0s3 
```

the 272GB is the linux partition and in disk utility ( the app) it dosent show up)

so i coant boot from the linux and i cant do enything but boot from live cd...

---

### Post by avtolle on 2009-03-13
I suggest taking a look at the Apple Users Forum for assistance with your problem. Link: [http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=328](http://ubuntuforums.org/forumdisplay.php?s=&daysprune=&f=328)

---

### Post by 0ra1suicid3 on 2009-03-13
ok thanks all post there
sorry for posting in wrong section

---

### Post by avtolle on 2009-03-13
This isn't necessarily the "wrong" section; it's just that you are likely to get more specialized assistance there.

---

