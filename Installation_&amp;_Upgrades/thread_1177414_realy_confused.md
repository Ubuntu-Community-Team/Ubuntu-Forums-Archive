---
title: "realy confused"
date: 2009-06-03
forum: Installation &amp; Upgrades
---

### Post by jaredhaddock on 2009-06-03
i got a new internal hard drive,the one that came with my pc. had vista built into it and it was only 160 g. so i got new one in . booted from my ubuntu disc and now cant downlaod vuze cant gdownload synaptic packs keep getting this message..

.W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/pool/multiverse/l/lsdvd/lsdvd_0.16-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/multiverse/l/lsdvd/lsdvd_0.16-3_i386.deb)
  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

---

### Post by dstew on 2009-06-03
It may be looking for the archive on a local DVD which is not there. You can uncheck the DVD search option in the System --> Administration --> Software Sources menu item. Then enable the Multiverse repository by checking the box. See [this documentation]("https://help.ubuntu.com/community/Repositories/Ubuntu").

---

