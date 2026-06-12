---
title: "fan runs all the time after upgrade to maverick 10.10"
date: 2010-10-12
forum: Hardware
---

### Post by nickleus on 2010-10-12
i have a Multicom Compal KHLB2 - 15.6" HD LED with an ATI Radeon HD 4650 graphics card

i'm wondering if my fan is running all the time because the proprietary ati driver doesnt work in 10.10 yet so i have uninstalled it. i dont remember ever hearing my fan in 10.4, when i was using this driver:
[http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx](http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx)
(i know about the hotfix for the newer kernels as well:
[http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx](http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx)
)

do you have to have a video driver to make the fan stop running?

---

### Post by veko on 2010-10-13
I have the same problem and I'd be interested to find a solution too.

I have Dell Studio 1555 laptop with ATI Mobility Radeon HD4000 series graphics card. After update to 10.10 Maverick, fan is spinnig all the time. On 10.04 and 9.10 it used to work well. 

I'm using open source fglrx-drivers instead of proprietary ones. Jockey suggests downloading ones, but I haven't tried that option yet. 

Otherwise Maverick works very nicely, just right out of the box. I'm amazed after all those problems I had with Lucid.

---

### Post by nickleus on 2010-10-13
> **veko said:**
> I have the same problem and I'd be interested to find a solution too.

I have Dell Studio 1555 laptop with ATI Mobility Radeon HD4000 series graphics card. After update to 10.10 Maverick, fan is spinnig all the time. On 10.04 and 9.10 it used to work well. 

I'm using open source fglrx-drivers instead of proprietary ones. Jockey suggests downloading ones, but I haven't tried that option yet.
the fan has quieted down now, seems back to normal actually after i installed the ubuntu fglrx driver (not the one from the amd site):
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/658170](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/658170)

---

### Post by nickleus on 2011-03-31
> **nickleus said:**
> the fan has quieted down now, seems back to normal actually after i installed the ubuntu fglrx driver (not the one from the amd site):
[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/658170](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/658170)
this was still a problem even with a clean install, at the end of maverick's lifetime (right before the release of 11.04). my cpu temperature was up to 55-56 C before it eventually would turn off my laptop automatically. i installed/enabled the amd driver by simply running:
```
jockey-gtk
```
and clicking the **Enable** button for the *ATI/AMD proprietary FGLRX graphics driver*

after restartiing, i rarely hear the fan anymore and my cpu temp is around 41 C =)

---

### Post by Yellow Pasque on 2011-03-31
Open-source radeon power management should be much better in Natty (assuming Ubuntu devs enable dynpm by default). [http://www.phoronix.com/scan.php?page=article&item=ati_linux_dynpm&num=4](http://www.phoronix.com/scan.php?page=article&item=ati_linux_dynpm&num=4)

On my RadeonHD 4250 laptop with Ubuntu 11.04, I still see better battery life with Catalyst, unfortunately. I'll have to test out the drivers more thoroughly, though and try another distro.

---

