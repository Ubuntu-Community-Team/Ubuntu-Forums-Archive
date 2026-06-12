---
title: "Mysterious name changing media"
date: 2008-07-31
forum: General Help
---

### Post by shortridge11 on 2008-07-31
I have 6 hdds in my computer- I'm running 7.10.  it's a home file server, and all was well.  Until now, i had no problems whatsoever, but for some reason when i reboot my box all the names of the hdds will swap around and not be mounted correctly because of this.  At first i thought it was a messed up fstab config, so i messed with it until everything matched up, and there were no inconsistencies.  So i rebooted my box again, and lo and behold they were all switched around again.  I used gparted to check out the 6 hdds, and i know they're moving around because my hdd that's partitioned into 3 parts keeps moving from sda to sdc to sdb, etc.  anyways- a while ago i installed psydm(maybe psdym?) and it helped configure my hdds.  However i think that it might be clashing with other things.  I tried uninstalling it the same way i installed it (apt-get) but it's not available to be uninstalled that way, and i don't know where it lives.

---

### Post by shortridge11 on 2008-07-31
My friend recommended that i change the fstab to boot them by UUID instead of dev, and so i'm trying that.

---

### Post by shortridge11 on 2008-07-31
I'm just not sure how my /dev can change things.  I've never heard of that before?  Once more, i change my fstab manually to mirror what it's set as, use mount and umount to mount and unmount them and figure out what they are, and then next restart it's all messed up again.

---

### Post by drs305 on 2008-07-31
I just wrote a tutorial on pysdm (see link in sig). It won't help if your devices are changing their designations and you aren't listing them as UUIDs or labels. If you use either of those two to identify the devices you should not experience the problems you are now.

If you reformat a partition the UUID will change and fstab would have to be edited but other than that it should work for you.

If you need any info on labeling partitions or getting the UUIDs there is info about 2/3 down the tutorial, or you can ask here.

PS I know that in Gutsy I used to have problems on rare occasions when a partition would change from *hdX* to *sdX* or vice versa. In Hardy and future releases all devices of this nature will be listed as *sdX*, which will also help.

---

