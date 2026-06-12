---
title: "external hdd"
date: 2007-07-02
forum: Hardware &amp; Laptops
---

### Post by mr.farenheit on 2007-07-02
i'm runnin an 80gb external hdd via usb connection for backing up my music and videos etc. my computer running xp has no problems what so ever reading the drive probably do to it being ntfs format. when i try and save files on to it which my notebook running ubuntu is says i don't have specific privledges to write to drive. i first saw this problem on ubuntu 6.06. the first time i conected to the drive and was able to save files easily. after that was when i started to receive the message. would it work easier if i were to format the drive to ext3 format and hope that i don't have the same problems with windows as i did ubuntu?

---

### Post by raja on 2007-07-02
Do you have ntfs-3g ? You cannot write to NTFS natively in Ubuntu.

---

### Post by mr.farenheit on 2007-07-02
no i prolly don't. where could i go to get it?

---

### Post by raja on 2007-07-02
```
sudo aptitude install ntfs-3g
```

You can also see [this.]("https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G")

---

