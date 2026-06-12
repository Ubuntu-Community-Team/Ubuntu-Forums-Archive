---
title: "HOWTO: HP Laserjet 1020 on Lucid"
date: 2010-08-17
forum: Hardware
---

### Post by zoubidoo on 2010-08-17
My HP laserjet 1020 was working fine up until 9.04 or 9.10 then it simply stopped working.  After three days of trawling and many months of printer downtime.  I found that two applications were trying to upload firmware to the printer: hplip and foo2zjs

The fix is very simple, allow only hplip to upload firmware. The following command prevents foo2zjs from uploading firmware:
```
sudo mv /etc/hotplug/usb/hplj1020 ~/
```

It took some time to find the problem because I was trying to solve usbfs: USBDEVFS_CONTROL failed cmd python rqt 128 rq 6 len 255 ret -110

For details see [https://answers.launchpad.net/hplip/+question/70357](https://answers.launchpad.net/hplip/+question/70357)

---

### Post by zoubidoo on 2010-12-27
See
[https://bugs.launchpad.net/hplip/+bug/500089](https://bugs.launchpad.net/hplip/+bug/500089)

---

