---
title: "Linux / *buntu on Samsung RV515"
date: 2011-06-22
forum: Hardware
---

### Post by omniuni on 2011-06-22
A $350 USD computer being sold at Best Buy, the Samsung RV515 features the new AMD Zacate e-350 APU. This combines two processing cores and a GPU on the same die.

I am working on this computer for a friend, and wanted to share the experience of dual booting Windows 7 Home Premium and KUbuntu.

Word of warning; Windows 7 has no drivers for this computer. You will need to install the wired or wireless network card driver manually, and then proceede with about 90 Windows updates before you have mostly working hardware if you choose to do a fresh install.

Thankfully, my Linux distro of choice, Kubuntu, proved the opposite.

All essential hardware was detected perfectly and completely. Graphics worked out of the box with full hardware acceleration including the blur shaders. Sound works fine (Internal and HDMI). The wireless card is an Atheros which also works out of the box with no additional work. The function keys work fine, etc, including software screen brightness. The webcam works fine, but be aware it does not have a hardware indicator when turned on.

Strangely, there is precisely one bit of hardware that is not detected... the touchpad. It seems to work just fine as a generic mouse, and I had not noticed that it wasn't techincally detected until I went into the touchpad configuration to see if I could enable two-finger scrolling.

Let me know if you have any questions or ideas. I will come back and update this post if I have any further info on the touch pad.

EDIT:
I believe the appropriate fix for the touchpad is here: [https://bugzilla.kernel.org/show_bug.cgi?id=27442](https://bugzilla.kernel.org/show_bug.cgi?id=27442)

It works fine for my friend, though, so I am not going to try it. If you own the laptop and have any success with it, please let me know.

---

### Post by mfeltman on 2011-07-27
Thank you so much for this post.  I'm planning an Ubuntu install on the one I just purchased, after I try out Windows 7 Premium, which I'm sure not to like...

---

### Post by siabost on 2012-01-31
Which version of Kubuntu did you install?

I have an Acer Aspire with Atheros 9285 Wi-Fi chip in it.
It works very slowly in Ubuntu 11.10 64bit and loses the connection regularly.

Thanks.

---

