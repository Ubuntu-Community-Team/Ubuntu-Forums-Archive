---
title: "Nvidia optimus"
date: 2011-11-11
forum: Hardware
---

### Post by stonemanhero on 2011-11-11
I tried this:
[http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/](http://www.ivegotavirus.com/blog/2011/11/06/how-to-get-optimus-working-on-ubuntu-11-10-oneiric/)


and everything was ok!

After rebooting i tried: optirun firefox 
and get this: 

The Bumblebee X server was not available, please check the
Bumblebee logfile at /var/log/bumblebee.log

and log:

[    309.58] Bumblebee log started at Fri, 11 Nov 2011 16:56:25 +0100
[    309.58] Creating fifo /var/run/bumblebee.fifo for communication...
[    309.65] Making FIFO writable for members of group bumblebee
[    309.66] Power management is disabled, not disabling card on start.
[    309.66] Waiting for orders
[    844.20] Checking for X server availability before stopping it...
[    844.21] The X server has not started or the pidfile is invalid.
[    844.22] X is stopped.
[    844.23] Power management is disabled, not unloading driver
[    844.24] Power management is disabled, card already enabled.
[    844.25] Bumblebee log ended on Fri, 11 Nov 2011 17:05:20 +0100
[     22.46] Bumblebee log started at Fri, 11 Nov 2011 17:06:37 +0100
[     22.46] Creating fifo /var/run/bumblebee.fifo for communication...
[     22.54] Making FIFO writable for members of group bumblebee
[     22.95] Unloading driver 'nouveau' on start...
[     23.26] rmmod /lib/modules/3.0.0-12-generic/kernel/drivers/gpu/drm/nouveau/nouveau.ko
[     23.26]   rmmod /lib/modules/3.0.0-12-generic/kernel/drivers/gpu/drm/ttm/ttm.ko
[     23.26]   rmmod /lib/modules/3.0.0-12-generic/kernel/drivers/platform/x86/mxm-wmi.ko
[     23.26] Disabling graphics card on start...
[     23.68] insmod /lib/modules/3.0.0-12-generic/updates/dkms/acpi_call.ko 
[     23.68] Waiting for orders
[    186.86] Optirun start request received.
[    186.86] Checking for X server availability before starting X...
[    186.87] X server is not started
[    186.88] Enabling graphics card...
[    187.51] 
[    187.52] Loading driver...
[    187.76] insmod /lib/modules/3.0.0-12-generic/updates/dkms/nvidia_current.ko 
[    187.76]   FATAL: Error inserting nvidia_current (/lib/modules/3.0.0-12-generic/updates/dkms/nvidia_current.ko): No such device
[    187.77] The driver failed to load.
[    187.78] Waiting for orders
[    245.05] Optirun start request received.
[    245.05] Checking for X server availability before starting X...
[    245.06] X server is not started
[    245.07] Enabling graphics card...
[    245.13] 
[    245.13] Loading driver...
[    245.39] insmod /lib/modules/3.0.0-12-generic/updates/dkms/nvidia_current.ko 
[    245.39]   FATAL: Error inserting nvidia_current (/lib/modules/3.0.0-12-generic/updates/dkms/nvidia_current.ko): No such device
[    245.39] The driver failed to load.
[    245.40] Waiting for orders
[    255.97] Optirun start request received.
[    255.98] Checking for X server availability before starting X...
[    255.98] X server is not started
[    255.99] Enabling graphics card...
[    256.05] 
[    256.05] Loading driver...
[    256.29] insmod /lib/modules/3.0.0-12-generic/updates/dkms/nvidia_current.ko 
[    256.29]   FATAL: Error inserting nvidia_current (/lib/modules/3.0.0-12-generic/updates/dkms/nvidia_current.ko): No such device
[    256.29] The driver failed to load.
[    256.30] Waiting for orders


Any help?

And 1 more question! How i can make unity effects to work?? Please help i can't make this optimus work....     :(:(:(:(:confused:

---

### Post by II Bo 247 II on 2011-11-11
What laptop are you trying to get it to run on and have you installed either Bumblebee or Ironhide in the past ??

---

### Post by stonemanhero on 2011-11-11
Dell N5110,  intel + nvidia  gt 525m ,Ubuntu 11.10 64bit
i installed bumblebee with step by step tutorial which i posted in first post.

---

### Post by II Bo 247 II on 2011-11-11
I see you've installed the restricted drivers... SavageCHRIS from ivegotavirus should be able to help you out then. that will most likely be your problem.

---

### Post by stonemanhero on 2011-11-11
ok. thank you!

---

