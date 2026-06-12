---
title: "[Kubuntu 14.04] Will Nvidia 173.14.39 on a GeForce4 bork it?"
date: 2014-04-22
forum: Hardware
---

### Post by zapjb on 2014-04-22
Specs: Asus a7n8x vm 400 with integrated Nvidia nforce2 graphics it is an integrated GeForce4 MX GPU.

I am not entirely satisfied with the nouveau driver. Not at all. The video twitching is bothersome. Small horizontal dashes flickering on & off. Every once in a while (rare) the video blinks on & off quickly.

So I know the nvidia-96 driver is not supported. But I tried anyways: sudo apt-get install nvidia-96. Couldn't find package. So a no go. Or probably not a good idea obtain it outside the repos?

Then I tried: sudo apt-get install nvidia-173. I said no at the confirmation prompt because I wanted feedback first.

I know the nivida-173 does not support my integrated GeForce4 MX at least from the literature I've read from Nvidia & elsewhere. But I want to try.

If the install even completes & that's a big if.

Will I bork my Kubuntu 14.04 install? Will Xorg not start? What might happen & can I easily recover? Should I try the official nvidia-96 from Nvidia?

Thanks.



Posted also at Kubuntu & Wilders Forums.

---

### Post by Yellow Pasque on 2014-04-22
Don't bother with the 173 driver. It won't work for Geforce4.

> Should I try the official nvidia-96 from Nvidia?
No, it's the same version (96.43.23) found in the Precise-proposed repository. Downloading it from Nvidia is not going to give it magic powers to work with the newer kernel/Xserver versions in Ubuntu 14.04

Your options are:
1) Make the best of nouveau driver
2) Install (K)Ubuntu 12.04.1 and use the nvidia-96 driver found in precise-proposed repo ( [https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.23-0ubuntu0.1](https://launchpad.net/ubuntu/+source/nvidia-graphics-drivers-96/96.43.23-0ubuntu0.1) )
3) Use generic/non-accelerated VESA driver

---

