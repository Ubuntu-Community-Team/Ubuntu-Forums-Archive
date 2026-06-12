---
title: "How to Install Radeon HD 5450 on Ubuntu 16.04"
date: 2017-09-02
forum: Hardware
---

### Post by ciscler on 2017-09-02
Hi all,
today I received my new graphics card Radeon HD 5450 which I will use on my ubuntu server 16.04. I have installed the driver but clinfo doesn't recognize the amd card. 
Can someone give me a hint? or can you recommand low budget amd graphic cards which will be supported by ubuntu 16.04?

Thanks in advanced

---

### Post by gsahli on 2017-09-02
So you used synaptic/apt/etc to install xserver-xorg-video-radeon ? You don't want fglrx or amdgpu.
Read this:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by him610 on 2017-09-02
Assuming your GFX card is properly connected, your Radeon HD 5450 should work fine using the Radeon driver in LTS 1604.

In Systems Settings, open Software & Settings, click on Additional Drivers tab - it will search for and display available drivers for your GFX card. Select the driver you want to be installed, and click 'Apply Changes.' Once the changes are applied, you will need to reboot.

---

### Post by kurt18947 on 2017-09-02
Are you sure you're not already using the radeon driver and don't even know it? I have an older AMD setup with HD3000 video. When I open a terminal and type "lsmod", I see this:

> radeon               1515520  3
i2c_algo_bit           16384  1 radeon
ttm                    98304  1 radeon
psmouse               131072  0
drm_kms_helper        155648  1 radeon


I did not install anything, the above is part of the default installation.

---

