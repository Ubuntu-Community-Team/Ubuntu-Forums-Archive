---
title: "1394 Firewire Drive does not mount in Gutsy or Hardy, OK in Feisty"
date: 2008-05-15
forum: Hardware
---

### Post by cojoco on 2008-05-15
I have an external hard drive which worked fine in Feisty using the 1394/Firewire interface.

Since upgrading to Gutsy and Hardy, this interface no longer works.

The USB-2 interface on the same drive works fine.

This is from /var/log/messages:

May 15 21:16:49 Jodie kernel: [406032.935355] scsi8 : SBP-2 IEEE-1394
May 15 21:17:10 Jodie kernel: [406053.901067] sbp2: probe of 0050770e00071002-0 failed with error -16
May 15 21:17:10 Jodie kernel: [406053.905874] scsi9 : SBP-2 IEEE-1394
May 15 21:17:31 Jodie kernel: [406074.870101] sbp2: probe of 0050770e00071002-0 failed with error -16
May 15 21:17:38 Jodie kernel: [406082.648587] scsi10 : SBP-2 IEEE-1394
May 15 21:17:59 Jodie kernel: [406103.819284] sbp2: probe of 0050770e00071002-0 failed with error -16
May 15 21:18:09 Jodie kernel: [406113.668710] scsi11 : SBP-2 IEEE-1394
May 15 21:18:30 Jodie kernel: [406134.635613] sbp2: probe of 0050770e00071002-0 failed with error -16

Can this be fixed?

Thanks!

---

### Post by Phobbes on 2008-07-08
I have the same problem on gutsy and hardy, but I never tried on feisty. If I boot the computer with the drive plugged in it mounts fine, but I can't plug it in once the computer is on.

---

### Post by ahickey on 2008-10-29
Just a little bit more information.

I have the same problem and having the drive plugeed in does allow it to mount.
I thought it might be a problem from the install, so I did a new install of 8.04.1 with the drive connected using Firewire and the problem persisted.
Drive plugged in on boot up - all OK
Drive plugged in after logging in - not working.

---

### Post by UtopiaTheory on 2008-10-29
Try this from a terminal:

```
sudo chmod 777 /dev/raw1394
```

Then:

```
sudo mount -a
```

Tom

---

