---
title: "How to switch laptop display to native resolution?"
date: 2012-12-10
forum: Hardware
---

### Post by redss on 2012-12-10
I have Ubuntu 10.04 loaded onto my older laptop HP Compaq nx6125 which has a native resolution of 1400x1050, but my monitor control panel doesnt let me switch to a resolution higher than 1024x768.

My laptop spec sheet says the graphics processor is ATI Mobility Radeon X300 and lspci says:
VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

I've tried manually adding the higher resolution using xrandr but switching to it locks up the computer.  So I apparently need to seek an alternative video driver.  

I have read that my graphics driver choices are the generic VESA driver, open source Radeon driver, Catalyst bbinary driver, or proprietary fglrx driver from AMD/ATI.  I've been unable to locate the proprietary driver which seems to be the ideal option, and I dont know which of the other drivers is in use.

How do I tell which video driver is in use, and any tips on how to get working in that native resolution or find a graphics driver that will work in ubuntu 10.04?

---

