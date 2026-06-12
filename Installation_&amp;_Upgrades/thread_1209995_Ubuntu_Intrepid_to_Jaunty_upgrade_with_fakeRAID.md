---
title: "Ubuntu Intrepid to Jaunty upgrade with fakeRAID?"
date: 2009-07-10
forum: Installation &amp; Upgrades
---

### Post by raistlin_kell on 2009-07-10
Have just built a Ubuntu Intrepid AMD64 vanilla build using the Alternative CD. PC has 4 x SATA HDD's and nVidia fakeRAID in the BIOS. Kernel 2.6.27.7 in vanilla boots perfectly, then upgraded to kernel 2.6.27.14 with synaptec & system still boots perfectly! (phew)

I'd like to upgrade to Jaunty 9.04 but have read (and experienced) the issues around RAID bugs with the 2.6.28.xx kernel. I know Jaunty uses these kernels & have read that some early distribution upgrades have disabled GRUB.

If i upgrade the Intrepid kernel to 2.6.2**9**.xx and the system still boots ok with fakeRAID, can i then upgrade from Intrepid to Jaunty with the newer kernel that normally comes with 2.6.2**8**.xx -or- will Jaunty disregard the newer kernel and install its own by default?

Can i just upgrade from Intrepid to Jaunty with the latest 2.6.2**8**.xx kernel and have fakeRAID boot ok? Does anyone know or attempted a system build/upgrade like this? 

Is there a better kernel to use that Jaunty will work with and fakeRAID is ok? 

Thoughts and opinions please. I'm looking for best methods to upgrade the distribution and still have a working fakeRAID array.

---

