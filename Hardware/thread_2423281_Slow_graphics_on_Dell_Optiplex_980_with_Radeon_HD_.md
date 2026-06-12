---
title: "Slow graphics on Dell Optiplex 980 with Radeon HD 3450 after upgrade to 18.04"
date: 2019-07-20
forum: Hardware
---

### Post by Alex_Filonov on 2019-07-20
I had 16.04 (stock install, open source drivers) on this PC for 2 years and it was working great. 1080 video played without delays or skips. Upgraded to 18.04, now 720 video plays almost OK (sometimes jumpy), 1080 all jumpy and skipping. Even Google Maps jumpy when trying to move a map.
Some data below:

 sudo lshw -C video[sudo] password for alex: 
  *-display                 
       description: VGA compatible controller
       product: RV620 LE [Radeon HD 3450]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:33 memory:e0000000-efffffff memory:f7df0000-f7dfffff ioport:dc00(size=256) memory:c0000-dffff

lsmod | grep radeon
radeon               1474560  24
ttm                   106496  1 radeon
drm_kms_helper        167936  1 radeon
drm                   401408  17 drm_kms_helper,radeon,ttm
i2c_algo_bit           16384  1 radeon


 
Any idea what's wrong. I'm almost ready to switch to onboard Intel video adapter, but want to use powerful card I have.

---

### Post by Autodave on 2019-07-22
Since no one else has jumped in, let me offer my 2 cents worth.  Download 18.04 and make a bootable USB or DVD and boot from that and see how your graphics are.  Upgrading from one version to another very often causes problems like this.  That is why I only do clean installs.  If your graphics work on a live session, my advice would be do back up everything to another drive and do a clean install of 18.04.

---

### Post by Alex_Filonov on 2019-07-24
OK, fixed it. It's bug  [1767468]("https://bugs.launchpad.net/ubuntu/+source/nux/+bug/1767468"). Happens you update 16.94 to 18.04 and remove Unity, I didn't remove Unity from my laptop, and it worked OK. When Unity removed, file 50_check_unity_support still remains in /etc/X11/Xsession.d and if Unity not found switches to generic drives, without hardware acceleration. Can happen with any graphic card, not only Radeon/AMD.

---

### Post by mastablasta on 2019-07-26
thank you for letting us know. i was just puzzled by the thread title since these chips have had descent support for some time now.

---

