---
title: "Video Driver for GMA3650"
date: 2013-03-21
forum: Hardware
---

### Post by wilsonmak on 2013-03-21
Did anyone install driver for GMA3650 successfully?
I try to install Ubuntu 12.04 on a DN2800MT with GMA3650 board.
The installation works fine.  And the system can find a new driver "Cedar Trial" from Ubuntu.  But after installation of driver, the system goes black screen.
And I can't boot the system again.

Any other proper GMA3650 drivers for Ubuntu?

Thanks in advance,
Wilson

---

### Post by Yellow Pasque on 2013-03-21
You're probably hitting this bug: [https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584](https://bugs.launchpad.net/ubuntu/+source/cedarview-drm-drivers/+bug/1132584)
Read that and see if the directions from Fred Moses help.

---

### Post by Rob Sayer on 2013-03-30
I had a similar problem with kubuntu on my cedarview netbook.  The thing was, the drivers were moved into the kernel but in a newer version than the one on the live install iso.

What worked for me was to install and then updating (through sudo apt-get update update manager) several times until I was sure I had everything.

Then installing the drivers through Additional Drivers worked.  The first one, it blanked the screen but after restarting it was fine.

---

### Post by wilsonmak on 2013-04-02
I've updated with sudo apt-get update......then added a new driver, but still have no luck to boot up to X Windows:

In the console
=========
# lsmod
ttm                    64734  1 cedarview_gfx
drm_kms_helper         32561  1 cedarview_gfx
drm                   196391  3 cedarview_gfx,ttm,drm_kms_helper
i2c_algo_bit           13199  1 cedarview_gfx
video                  19115  1 cedarview_gf

# tail -f /var/log/kern.log
Apr  2 18:54:26 localhost kernel: [    8.207157] Xorg:1226 conflicting  memory types 7f800000-7ffe9000 write-combining<->uncached-minus
Apr  2 18:54:26 localhost kernel: [    8.207169] reserve_memtype failed  0x7f800000-0x7ffe9000, track uncached-minus, req uncached-minus
Apr  2 18:54:26 localhost kernel: [    8.225441] init: lightdm main process (1212) terminated with status 1

Any clues?

---

### Post by Rob Sayer on 2013-04-03
I should have said sudo apt-get update AND update manager instead of "sudo apt-get update update manager".  In my case (kubuntu) the latter equivalent is muon update manager.

You probably need to get a newer kernel version for the cedar trail drivers to work.  apt-get update won't do this.  I had the same thing happen with my atom 2600/cedartrail netbook installing ubuntu.  It bricked the video unless I updated everything before installing the cedarview stuff in additional drivers.  With both terminal and update manager.

In my naivete I had originally assumed that if you install additional drivers from system settings it'll tell you if you need to have a newer kernel or other package first, like synaptic package manager would.  It doesn't.

---

### Post by wilsonmak on 2013-04-08
Yes I have already upgraded to the latest kernel and patches from synaptics update manager before installing the new driver.  But still, I have no luck to get it working.  

1) I try to upgrade the new driver with "Add New Hardware"

2) I try to manually install the driver:
sudo apt-get install cedarveiw-drm cedarview-graphics-drivers libva-cedarview-vaapi-driver

---

### Post by rudylar on 2014-01-15
Do you guys have some news about that issu ?

I tried to install the last 13.10 Ubuntu version but it is even worse. I think 3D feature in Ubuntu is activated in standard.

---

