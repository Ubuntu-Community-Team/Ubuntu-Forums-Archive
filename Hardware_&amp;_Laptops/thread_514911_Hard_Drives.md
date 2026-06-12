---
title: "Hard Drives"
date: 2007-08-01
forum: Hardware &amp; Laptops
---

### Post by Holmes89 on 2007-08-01
I am using an old 20 gig hard drive to experiment with Ubuntu, I realized that I loved it and wanted to get a better drive to run it, so I purchased an 80 gig hard drive. I just got all of my settings to work and the way I want them so I would like to migrate all of this work to my new drive without having to start from scratch. Does anyone know how I would be able to do this?

---

### Post by hysteresis on 2007-08-01
from your livecd, you should be able to do the dd command in a terminal. You must be su, so I think you have to  type "sudo su" to get the root prompt.
dd  bs=32k if=/dev/hda of=/dev/hdb

in this example /hda is your 20GB drive and /hdb is your 80GB drive. Your drive assignments may be different. it will probably make your 80GB drive look like a 20GB drive, so then you will have to use download gparted to change your partition size.

---

