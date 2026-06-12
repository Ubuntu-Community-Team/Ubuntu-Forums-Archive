---
title: "Swapped HDMI lead for DDP and now have no resolution control"
date: 2021-09-30
forum: Hardware
---

### Post by makem2 on 2021-09-30
I have been using a MSI monitor with 20.04 without making any changes to the default resolution settings and it worked fine with and HDMI to HDMI cable.

I changed the cable for a Display Port to Display Port cabl**e** and now have no control over the resolution which is set at 1024 x 768 and as such is unusable.

I made sure all software was up to date.

I am using an integrated GPU, Intel UHD Graphics 630.

I am currently awaiting debugging because I am told the  kernel driver  hasn't loaded correctly.

This information comes from:

[https://github.com/intel-gpu/documentation/issues/14](https://github.com/intel-gpu/documentation/issues/14)

The latest reply is:

"Thanks, provided logs were helpful. We can confirm that kernel driver  hasn't loaded correctly on you system. In order to speed up debug and  resolution we are going to reproduce this problem and debug further."

With that in mind, if it was working with HDMI, should the Display Port to Display Port cabl**e**  cripple it?

I connected another ASUS monitor using an HDMI cable whilst the Display Port to Display Port cabl**e**  connected monitor was still connected and I don't even get the same result I had previously with HDMI. All I get is an identical desktop with the same 1024 x 768 resolution which cannot be changed either. Nor does the second monitor show on the ubuntu 'Display' settings.

Is this related to the kernel driver issue and should I just give up with Display Port to Display Port cabl**e** until that is solved?

---

