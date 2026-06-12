---
title: "Hard Drive is not recognized"
date: 2012-10-26
forum: Hardware
---

### Post by blade9753 on 2012-10-26
I have an older desktop, to whose hard drive has wiped. I installed ubuntu from a boot cd to a usb flash drive. I want to take the hard drive and create 2 partions on it (one for storage, one for ram). However, ubuntu does not recognize the hard drive. Any suggestions?

---

### Post by 2F4U on 2012-10-27
So you are able to boot Ubuntu on the desktop from either the usb or cd media? Can you start the installation process or the live system? Can you post a screenshot of the partitioning tool? Did you verify the physical connections of the hard drive?

---

### Post by blade9753 on 2012-10-27
I can boot from the flash drive i installed it to. When i first attempted to install ubuntu it recognized the hard drive, and i have just checked, the hard drive is connected. However when i first installed it said that the boot cd was made too quickly, and after that i have not been able to read the hard drive.

---

### Post by 2F4U on 2012-10-27
> However when i first installed it said that the boot cd was made too  quickly, and after that i have not been able to read the hard drive.

Could be an indication of a bad burn. If you are still using the same, I would suggest to create new boot media.

---

### Post by blade9753 on 2012-10-27
I did create a new disk, and that is how i installed. But now the computer does not recognize the hard drive.

---

### Post by NetGO on 2012-10-28
Try Gparted.

I had same experience. But in my case gparted recognized it. So make partition and and filesystem with Gparted. Then it mounted.

After that I modified fstab to mount it.

---

