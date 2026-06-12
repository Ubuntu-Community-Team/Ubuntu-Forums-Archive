---
title: "Playing DVD from external DVD Recorder"
date: 2008-10-22
forum: Hardware
---

### Post by salemboot on 2008-10-22
The drive is an I/O Magic.

The problem is when I want to watch a DVD it stalls and spews numerous errors to the console.

[ 1115.164944] end_request: I/O error, dev sr1, sector 1715076
[ 1115.403937] end_request: I/O error, dev sr1, sector 1715084
[ 1115.553318] end_request: I/O error, dev sr1, sector 1715084
[ 1115.792184] end_request: I/O error, dev sr1, sector 1715092
[ 1115.941440] end_request: I/O error, dev sr1, sector 1715092

From reading the few posts available of people having the same problems I know it may be an incompatibility with the enclosure.

But why would this matter?   Otherwise the drive works fine with reading and burning with command line tools.

The next problem is K3B.   It scans the hardware and disables the drive.  It seems as though its trying to access some high-level feature of the drive which the scsi emulation/usb isn't capable of providing.

Any clues?

Thanks

---

