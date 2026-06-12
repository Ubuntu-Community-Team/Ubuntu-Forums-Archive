---
title: "Ubuntu AMD 64 md5 failing"
date: 2005-01-05
forum: Installation &amp; Upgrades
---

### Post by Qazumation on 2005-01-05
I just downloaded the AMD 64 ubuntu iso twice. After burning each time, the md5 check fails on the CD.  The md5 does not fail on the iso, but the files after burning.

Is it safe to install? Why is it doing this?

Here's what failed:
```

./dists/testing/main/binary-amd64/Release: FAILED open or read
./dists/testing/main/binary-amd64/Packages: FAILED open or read
./dists/testing/main/binary-amd64/Packages.gz: FAILED open or read
./dists/testing/main/debian-installer/binary-amd64/Packages: FAILED open or read
./dists/testing/main/debian-installer/binary-amd64/Packages.gz: FAILED open or read
./dists/testing/restricted/binary-amd64/Release: FAILED open or read
./dists/testing/restricted/binary-amd64/Packages: FAILED open or read
./dists/testing/restricted/binary-amd64/Packages.gz: FAILED open or read
./dists/testing/Release: FAILED open or read
./dists/local/main/binary-amd64/Release: FAILED open or read
./dists/local/main/binary-amd64/Packages: FAILED open or read
./dists/local/main/binary-amd64/Packages.gz: FAILED open or read
./dists/local/main/debian-installer/binary-amd64/Packages: FAILED open or read
./dists/local/main/debian-installer/binary-amd64/Packages.gz: FAILED open or read
./dists/local/restricted/binary-amd64/Release: FAILED open or read
./dists/local/restricted/binary-amd64/Packages: FAILED open or read
./dists/local/restricted/binary-amd64/Packages.gz: FAILED open or read
./dists/local/Release: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/cdrom-core-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/firewire-core-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/floppy-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/ide-core-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/nic-extra-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/nic-pcmcia-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/nic-shared-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/nic-usb-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/parport-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/pcmcia-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/pcmcia-storage-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/scsi-common-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/scsi-core-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/scsi-extra-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/serial-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/socket-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read
./pool/main/l/linux-kernel-di-amd64-2.6/usb-storage-modules-2.6.8.1-3-amd64-generic-di_0.14ubuntu12_amd64.udeb: FAILED open or read

```

Edit: The data was verifed and passed perfectly both times, I used CD-Rs of a good brand, and the files that failed were always the same.

---

### Post by sfabel on 2005-09-27
I can confirm this with the newest Breezy preview ISO. Exact thing happened to me, although I haven't verified the specific files on the CD-ROM.

I'm now trying to fall back to the hoary install iso, I hope that works.

Stephan

---

