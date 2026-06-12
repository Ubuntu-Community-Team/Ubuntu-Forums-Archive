---
title: "Ubuntu 15.10 and six monitors?"
date: 2016-03-18
forum: Hardware
---

### Post by Drenriza on 2016-03-18
Hi all

I am to setup a work area with six monitors (for myself) and would like to use Ubuntu 15.10 for this.
My question in this regard, is if anyone can advice on a GFX that works out of the box with such a setup.

Is 1x AMD with EyeInfinity and display ports the way to go to run them as six individual screens?
The screens i would like to use are 6x Dell U2515H

Also anyone who can advice on a good monitor stand for such a setup? That also support horizontal, vertical alignment along with tilt.
I have Googled (alot) and found [http://www.wsgf.org/products/wsgf-mega-desk-stand-v2](http://www.wsgf.org/products/wsgf-mega-desk-stand-v2)

Anyone with direct experience who would like to share? :)

Thanks on advance!

---

### Post by QIII on 2016-03-18
Eyefinity does work with the proprietary fglrx driver and you should be able to run 6 monitors if you have either 6 DP ports or can split the signals if you have fewer.  

Using the open source driver, I am able to use the three monitors I have.  That may be true for 6 monitors, but I believe Eyefinity is required for > 3 monitors.  I may be mistaken.  

You should be aware of a few of considerations:

1.  15.10 is not an LTS (Long Term Support) release and will go out of support in July.  Thus, it is probably not a good choice for a mission-critical system.

2.  The proprietary fglrx driver ***WILL NOT WORK*** with 16.04, which is the upcoming LTS.  There is a huge change happening in the environment of drivers in Linux for AMD products and the fglrx driver is going away in favor of the open source AMDGPU driver which is a joint effort by AMD and the open source community.  However, it is not expected to be fully functional (it mostly works now, however) until later this year.  This means that it is likely that some functionality/customization may not be present.  Right now I am able to run 3 monitors in 16.04, but I can't say for sure that 6 will work.

3.  If this is a critical machine and you must be sure it will work with all six monitors -- and want to use the current fglrx driver -- then you may want to consider installing 14.04 and ***NOT*** installing any of the Hardware Enablement Stack (HWE) packages.  The current HWE stacks all go out of support in July, when a new HWE stack will come out and that will not work with fglrx, either.

---

### Post by Drenriza on 2016-03-19
Thanks for your reply QIII!!

My understanding from your post
--------------------------------
Partial success.
I should run Ubuntu 15.04 with the fglrx driver to be able to connect six monitors (and treat them at six individual monitors, i dont want to run them as a "single" large monitor) since this is the driver that is supported in 15.04 that has Eyefinity.
And then when the 16.04 driver becomes fully functional i can consider upgrading?

The more guranted success.
Downgrade to 14.04 and avoid the HWE packages under the installation process?

---

### Post by Drenriza on 2016-03-19
EyeInfinity and display ports question.

When you buy a GFX card that has two display ports, but allow six monitors to connect. How does that work, anyone?
Do you daisy chain the monitors, 3x monitors to one display port. But how does the software keep track of three screens
through one port?

Or if your GFX has 2x display ports do you purchase 2x Multi Stream Transport (MST) hubs toget six "individual" ports?
[http://www.club-3d.com/index.php/products/reader.en/product/mst-hub-1-3.html](http://www.club-3d.com/index.php/products/reader.en/product/mst-hub-1-3.html) Do Ubuntu like these kind of hubs?

To avoid a setup configuration nightmare (and i don't do graphical work), would it make more sense to just buy the older Radeon HD 5870
which has six seperated mini display ports and than connect all the monitors to their individual port?

Anyone who has experience with these two ways of doing it?

---

### Post by QIII on 2016-03-19
Do not, under any circumstances, attempt to use 15.04.  It is no longer supported.

For a mission-critical machine using AMD graphics, I would go with 14.04.1, which is a Long Term Support release supported until April 2019.  Do not apply any of the HWE packages.

As far as 16.04 -- it will not support fglrx at all, ever.  Neither AMD nor Canonical want to commit to maintaining fglrx for the graphics stack in 16.04.  We'll have to see how AMDGPU works out.

*Depending on the capabilities of the GPU in terms of max resolution* and whether or not MST is supported, you can daisy chain DP monitors, but typically 3 per DP port on the card, max.  That is something you will have to research on a per-card basis.  You'll also need to be sure that MST is supported in any hardware connected.

A 5870 might work, but that technology is getting long in the tooth and the "tree" chips (I think the 5870 is a Cypress) may not work with AMDGPU.  This is a troubled time.  The open source community has been pestering AMD for a really good open source driver and we are going to get it, it seems.  Unfortunately, that may mean some (more) products get left behind.  (As an aside, for a long time I used a system with 4x 5870s for a parallel processing project.  I'd turn it on and the lights in the neighborhood would dim.)

Also consider NVIDIA products.  They are not my area of expertise, so I can't really advise there.

---

### Post by Drenriza on 2016-03-21
Thanks Qlll ! I really appreciate the feedback.

---

