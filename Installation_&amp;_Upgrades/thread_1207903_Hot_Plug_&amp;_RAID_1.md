---
title: "Hot Plug &amp; RAID 1"
date: 2009-07-08
forum: Installation &amp; Upgrades
---

### Post by carl_76 on 2009-07-08
Hi.

I am running 9.04 on a laptop.  I have 2 identical USB drives attached and the /home directory is a RAID 1 configuration between the /home partition on the laptop hd and the two external drives.  It is also encrypted.  It installed fine and boots fine.  However....

I tested booting the laptop without the 2 external drives using the process described in the HotplugRaid wiki page:  [http://wiki.ubuntu.com/HotplugRaid](http://wiki.ubuntu.com/HotplugRaid)  This involved using the mdadm --run command to start the raid device and then allowing the boot to proceed to the login screen, and then rebooting.  On the second boot, after the array was started, it would boot and operate fine.

Since then, this process no longer works.  After the reboot the raid device status is inactive.  I had installed all the updates after I did the degraded boot test so I'm wondering if one of the updates stops the raid array on reboot.

Basically, I'd like to know if anyone has a solution to allow me to boot the laptop without the external drives attached.

Thanks in advance, and let me know if you need more information.

---

