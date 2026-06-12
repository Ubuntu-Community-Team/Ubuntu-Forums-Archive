---
title: "Booting From Wrong Drive"
date: 2012-02-11
forum: Hardware
---

### Post by 3D Peruna on 2012-02-11
I recently installed oneiric (11.10) server on a new system.  However, I need to get data off the old drive (motherboard, power supply, and video card all died at once after about 7 years of continuous use).

Pull out the old drive, put it in the new machine and boot up.  GRUB comes up with the correct menu, then proceeds to use the old drive to boot from.  What gives?

What do I need to do to be able to read the old drive from the new install?

---

### Post by ahallubuntu on 2012-02-11
Connect up the drives in a way that makes sure /dev/sda is the new drive - so on the motherboard, make sure the new drive is connected to the first SATA connector ("SATA0") on the motherboard.  The other drive can be conencted to SATA1 or whatever additional SATA connectors there are.

But if the old drive is PATA (IDE/flat ribbon cable), you may need to do something else in the BIOS to make sure SATA drives (assume new one is SATA) are ordered before PATA.

Or, boot your your live CD with the drives as they are and do an update-grub using the chroot method, to get Grub to recognize the new drive configuration.  Or just copy off your old data using the live CD (otherwise, if you remove old drive, you  may have to run update-grub again.)

---

### Post by 3D Peruna on 2012-02-11
Thanks!  The DUH! moment always comes right after you read the reply!

Boot from CD is the way to go, I think!

---

