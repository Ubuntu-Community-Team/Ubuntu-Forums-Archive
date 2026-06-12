---
title: "K3b dvd burn verify failed"
date: 2009-01-01
forum: Hardware
---

### Post by logos34 on 2009-01-01
Yet another dvd coaster...

These are freakin Verbatim dvd+r, why o why is it failing to verify? I burned them slowly (4x), and dvd+rw works perfectly

Can anyone tell me if the errors only effect the the end of the disc (sectors 2000000+)?  How to tell which files are in which dvd sector?

> ate finish Wed Dec 31 18:27:35 2008
[mkisofs]  99.87% done, estimate finish Wed Dec 31 18:27:35 2008
[mkisofs]  99.90% done, estimate finish Wed Dec 31 18:27:34 2008
[mkisofs]  99.92% done, estimate finish Wed Dec 31 18:27:34 2008
[mkisofs]  99.94% done, estimate finish Wed Dec 31 18:27:34 2008
[mkisofs]  99.96% done, estimate finish Wed Dec 31 18:27:35 2008
[mkisofs]  99.98% done, estimate finish Wed Dec 31 18:27:35 2008
[mkisofs] Total translation table size: 0
[mkisofs] Total rockridge attributes bytes: 91707
[mkisofs] Total directory bytes: 190180
[mkisofs] Path table size(bytes): 1918
[mkisofs] Max brk space used c5000
[mkisofs] 2282902 extents written (4458 MB)
[K3bIsoImager] Pipe throughput: 4675383296 bytes read, 4675383296 bytes written.
[growisofs]  4648402944/4675383296 (99.4%) @3.9x, remaining 0:05 RBU  80.5% UBU  55.1%
[growisofs]  4666884096/4675383296 (99.8%) @4.0x, remaining 0:01 RBU  25.4% UBU  61.2%
[growisofs] /dev/scd0: flushing cache
[growisofs] /dev/scd0: closing track
[growisofs] /dev/scd0: closing disc
[COLOR="Red"][K3bDataTrackReader] reading sectors 0 to 2282901 with sector size 2048. Length: 2282902 sectors, 4675383296 bytes.
[K3bDataTrackReader] using buffer size of 64 blocks.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2003264.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2032960.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2043520.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2052480.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2063168.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2084608.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2091648.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2100096.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2107648.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2154752.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2154816.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2156160.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2158848.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2159296.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2159552.
[K3bDataTrackReader] Problem while reading. Retrying from sector 2162496.
[K3bDataTrackReader] Read error in sector 2162512.
[K3bDataTrackReader] Read a total of 2162496 sectors (4428791808 bytes)[/COLOR]

---

### Post by frogotronic on 2009-06-17
It's not you - its K3B ; its a known bug

[https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/362337](https://bugs.launchpad.net/ubuntu/+source/k3b/+bug/362337)

---

