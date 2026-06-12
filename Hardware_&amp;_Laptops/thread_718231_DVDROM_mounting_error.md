---
title: "DVDROM mounting error"
date: 2008-03-07
forum: Hardware &amp; Laptops
---

### Post by grawr on 2008-03-07
When I try and mount my dvdrom drive(which is /etc/hdc) it says this:

#mount: block device /dev/hdc is write-protected, mounting read-only
#mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

then when i type dmesg | tail, it says:

[17211004.264000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
[17211004.304000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
[17211006.336000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
[17211006.372000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
[17211008.392000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
[17211008.428000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
[17211010.424000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
[17211010.492000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
[17211012.488000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00
[17211012.520000] hdc: error code: 0x70  sense_key: 0x02  asc: 0x06  ascq: 0x00

---

### Post by Trimesh on 2008-03-08
Sense key 02 is "Not ready" - either there is no medium in the drive, it's a disk that the drive can't read, or it's broken.

---

