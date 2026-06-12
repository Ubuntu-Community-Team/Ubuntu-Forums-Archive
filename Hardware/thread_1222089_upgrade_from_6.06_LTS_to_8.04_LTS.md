---
title: "upgrade from 6.06 LTS to 8.04 LTS"
date: 2009-07-24
forum: Hardware
---

### Post by ajaustin on 2009-07-24
Just to report that everything went fine!!

I followed the instructions on the Ubuntu web site, downloaded the 8.04-386 alternate CD iso and ran it.  Most of the upgrade was done from the CD and then some more via Internet.  Everything seems to work fine with a minimum of after-tweaking.

I had to re-setup the Synaptics Touchpad on my HP nx8820 with gsynaptics as options are no longer taken from /etc/xorg.conf.

I had been worried that my RAID 1 (mirroring) would be a problem as I had retro-fitted it to 6.06 LTS using a HOWTO for Red Hat!!  It didn't work right off but, and I'm no guru, a little bit of fiddling with /etc/fstab and /etc/raidtab to get it working with /dev/sda, /dev/sdb instead of /dev/hda, /dev/hdb seems to have done the trick and the array has resynced OK.

Other than that all the core stuff and apps have been smoothly upgraded.  I hope all goes as well when I have to go to the 2011 LTS.

Thanks Ubuntu people!

Tony

---

