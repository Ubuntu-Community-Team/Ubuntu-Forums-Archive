---
title: "Proliant 5500 with Smart Array 3200"
date: 2009-02-17
forum: Hardware
---

### Post by skigeoff02 on 2009-02-17
I sucessfully installed Ubuntu 8.10 from the server iso on a Compaq Proliant 5500 with a SmartArray 3200 RAID controller.

After setting up the array with the SmartStart CD I booted off the Ubuntu Server CD.  NOTE: When partitioning the disks in the Ubuntu installer you must partition manually using care not to remove the Compaq System Utility Partition.  

After the install completes the system will fail to boot.  To correct this, boot from CD again and run the rescue option, make your partition containing your / (or /boot) bootable.  You must then select the rescue option to reinstall grub.  Install grub to the partition that you just made bootable.  Reboot and you're in business.

Good luck!

---

