---
title: "ATI 5730 video card compatibility issue"
date: 2010-05-03
forum: Hardware
---

### Post by Jon_Samuelson on 2010-05-03
First off let me apologize for the fact that this is in many ways a repost of a problem I've seen elsewhere on these forums.  I'm an Ubuntu (and in many ways a Linux) newbie though, so I'm just a little nervous applying a fix I'm not 100% certain is applicable for my situation.

I recently bought a new laptop, and ASUS with an ATI 5730 video card with 1GB of dedicated video memory.  I installed Ubuntu 9.10, and with the default video drivers I only had 1152x864, 1024x768, and 800x600 as resolution options.  The screen however is 16:9 ratio, and supports up to 1600x900 resolution.  Ubuntu suggested I install the proprietary drivers, which I did.  Doing so resulted in being able to use the native 1600x900 resolution, but also in an annoying watermark in the lower right-hand corner of the screen, stating "AMD Unsupported hardware".  I would like to get rid of that thing, if possible.

I'll include here the results of a couple of command line inquiries I've heard are relevant for ID of the video card, and drivers...

jon@Valhalla:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Madison [Mobility Radeon HD 5000 Series]

jon@Valhalla:~$ sudo lshw -C video
  *-display             
       description: VGA compatible controller
       product: Madison [Mobility Radeon HD 5000 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:37 memory:c0000000-cfffffff(prefetchable) memory:d0020000-d003ffff ioport:d000(size=256) memory:d0000000-d001ffff(prefetchable)

Any help you guys can give me will really be appreciated.  I'd hate for something stupid like this to mar my enjoyment of Ubuntu.

---

### Post by Jon_Samuelson on 2010-05-04
I don't want to bump my own thread, but...

---

### Post by areskz on 2010-07-07
You are lucky that you succeeded in installing proprietary drivers. I didn't. X didn't load after installing, so I had to track back.

I am using Mobility 5730 with 1GB as well.

One thing I figured out is that ATI stopped developing proprietary driver, and now they only develop open source one, but it still can't give us full performance. Bite me if I am wrong.

---

### Post by Pifilatakanemu on 2011-02-23
Any news on this?

---

### Post by areskz on 2011-07-26
Anyone knows how to install ati 5730 drivers on Ubuntu-based distros?

---

