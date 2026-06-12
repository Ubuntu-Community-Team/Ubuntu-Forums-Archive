---
title: "Nvidia 970M installed, graphics running at a crawl"
date: 2015-03-20
forum: Hardware
---

### Post by rohan8 on 2015-03-20
Hi

A little while back I got the nvidia 346.47 drivers from xedgers installed and working, or so I thought! (maybe they are working, stuck here)
It "seems" they are working(I think), but every application that needs 3d acceleration runs at a crawl, even slower then when running with the nouveau drivers.

I run 'dpkg -l | grep nvidia' to check my nvidia drivers installed: 
[B]ii  nvidia-346                                  346.47-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA binary driver - version 346.47
ii  nvidia-346-uvm                              346.47-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA Unified Memory kernel module
ii  nvidia-opencl-icd-346                       346.47-0ubuntu1~xedgers14.04.1                         amd64        NVIDIA OpenCL ICD
ii  nvidia-prime                                0.6.2                                                  amd64        Tools to enable NVIDIA's Prime
ii  nvidia-settings                             346.47-0ubuntu1~xedgers14.04.1                         amd64  [/B]

To test the speed I ran glxgears, which gave me : 
[B]4549 frames in 5.0 seconds = 908.683 FPS                                                                          
4101 frames in 5.0 seconds = 819.759 FPS                                                                          
4970 frames in 5.0 seconds = 993.953 FPS                                                                           
4612 frames in 5.0 seconds = 922.297 FPS                                                                           
4374 frames in 5.0 seconds = 872.581 FPS                                                                            
4471 frames in 5.0 seconds = 891.499 FPS                                                                            
4691 frames in 5.0 seconds = 938.194 FPS [/B]

Any ideas what the problem could be?

---

### Post by dino99 on 2015-03-20
at time, vivid archive has a better/newer/fixed 346.47-0ubuntu4 driver, where the 'uvm' package is gone (unified with main package now)
so purge the xorg-edgers one first (ppa-purge) then install from the archive (synaptic)

---

### Post by rohan8 on 2015-03-20
I have Kubuntu 14.10 currently installed. Is this the Vivid "15.04" version archive you are talking about?

---

### Post by dino99 on 2015-03-20
> **rohan8 said:**
> I have Kubuntu 14.10 currently installed. Is this the Vivid "15.04" version archive you are talking about?

yep

---

### Post by rohan8 on 2015-03-20
But will this version in the vivid archive actually work in 14.10, or will I have to upgrade to 15.04 to test it out then?

---

### Post by dino99 on 2015-03-20
you can indeed download and use the vivid version: [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-346](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-346)
or directly upgrade to vivid, which very stable (i'm using it daily since a few months), by changing 'utopic' by 'vivid' inside /etc/apt/sources.list, then update and upgrade (but first disable all extra/exotic repo like ppa)
you should get better performance with your recent hardware.

---

### Post by rohan8 on 2015-03-20
Gave the upgrade a go as I've tried almost everything to get it working properly in 14.10.
15.04 - > the 970M still not being used in applications that need it, tried all the synaptic 346.47 drivers, and steam is not working now :(

Any other ideas?

---

