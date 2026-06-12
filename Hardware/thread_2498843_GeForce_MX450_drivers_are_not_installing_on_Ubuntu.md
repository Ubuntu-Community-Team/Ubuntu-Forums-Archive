---
title: "GeForce MX450 drivers are not installing on Ubuntu 24.04"
date: 2024-06-30
forum: Hardware
---

### Post by gvais on 2024-06-30
Hello!

Notebook IdeaPad 5 Pro 14ITL6
GeForce MX450
Ubuntu 24.04

I tried installing all possible drivers: 535, 545, the ones recommended by the system, and followed all the guides I could find. I sent the errors to the GPT chat, but the result is the same - no drivers are being installed.
I am getting various errors, for example:

```
ERROR: Cannot create report: [Errno 17] File exists: '/var/crash/nvidia-dkms-545.0.crash'Error! Bad return status for module build on kernel: 6.8.0-36-generic (x86_64)Consult /var/lib/dkms/nvidia/545.29.06/build/make.log for more information.dpkg: error processing package nvidia-dkms-545 (--configure): installed nvidia-dkms-545 package post-installation script subprocess returned error exit status 10dpkg: dependency problems prevent configuration of nvidia-driver-545: nvidia-driver-545 depends on nvidia-dkms-545 (<= 545.29.06-1); however:  Package nvidia-dkms-545 is not configured yet. nvidia-driver-545 depends on nvidia-dkms-545 (>= 545.29.06); however:  Package nvidia-dkms-545 is not configured yet.dpkg: error processing package nvidia-driver-545 (--configure): dependency problems - leaving unconfiguredNo apport report written because the error message indicates its a followup error from a previous failure.          Processing triggers for initramfs-tools (0.142ubuntu25.1) ...update-initramfs: Generating /boot/initrd.img-6.8.0-36-genericErrors were encountered while processing: nvidia-dkms-545 nvidia-driver-545E: Sub-process /usr/bin/dpkg returned an error code (1)
```

and other errors.

---

### Post by deadflowr on 2024-06-30
What does the make log tell you?
/var/lib/dkms/nvidia/545.29.06/build/make.log

---

### Post by Yellow Pasque on 2024-06-30
Don't use Nvidia 545. It hasn't been updated since last year. Most, likely, you are hitting this bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-545/+bug/2065139](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-545/+bug/2065139)

Either use the 535 "long-lived" branch or the 550 branch

---

### Post by gvais on 2024-07-01
Disabling secure boot helped me. After that, the driver worked normally

---

