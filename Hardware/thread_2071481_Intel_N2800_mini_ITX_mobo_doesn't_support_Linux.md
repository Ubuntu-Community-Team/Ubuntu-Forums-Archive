---
title: "Intel N2800 mini ITX mobo doesn't support Linux"
date: 2012-10-15
forum: Hardware
---

### Post by jynyl on 2012-10-15
I bought an Intel mini-ITX DN2800MT motherboard to make a HTPC system, as it looked like a good fanless system, and Intel had a case study showing it worked with Linux, and offered Linux drivers on the website.
[http://download.intel.com/support/motherboards/desktop/sb/enabling_hardware_accelerated_playback_ubuntu_12.pdf]("http://download.intel.com/support/motherboards/desktop/sb/enabling_hardware_accelerated_playback_ubuntu_12.pdf")

But after much mucking around, it appears this series uses Cedarview (aka Cedar Trail) and does not support Linux.

The Intel case study says it is for Ubuntu 12, but the instructions say to compile a 3.1 kernel (12.04 uses 3.2) while the illustrations in the instructions appear to be from a 3.0 kernel.  Following the instructions didn't give a working system.

Ubuntu 12.04 offers cedarview drivers, but they don't work on this system.  (12.04 runs xorg but without hardware graphics acceleration, which makes it useless for HTPC.)
Ubuntu 12.10 beta 2 says it doesn't have any cedarview drivers.

But if I've missed something and this mobo can work with Linux, please advise.  Otherwise, beware of Intel mini-ITX boards.

---

### Post by pascal_dher on 2012-11-01
Have you tested with final ubuntu 12.10 ?

I recently saw a canonical presentation of "new in 12.10" and cedar trail was listed as a point. 
I'm thoroughly considering buying one - but of course it has to have proper hardware support.

---

### Post by pascal_dher on 2012-11-01
BTW: The driver is only available for 32 bit. (did you try with 12.10 64 bit?)

---

### Post by jynyl on 2012-11-02
Yes, I tried with 32 bit versions of 12.04, 12.10 beta2 and Arch Linux.  But haven't tried with the final edition of 12.10, so I must find time soon.

---

### Post by jynyl on 2012-11-03
With Ubuntu 12.10, the installer runs the display ok (it didn't with beta 2), but fails during restart after install.  Just get black screen with blinking cursor, no keyboard response.

Reboot to failsafeX mode asks about continuing to remount / filesystem in read/write mode, then freezes.

---

### Post by BicyclerBoy on 2012-11-03
Kernel 3.5 & latest intel drivers are available on xorg-edgers ppa..

I doubt you will get any joy with old kernels..

You may need to boot with nomodeset **just** to get to the desktop..
Grub boot option "nomodeset" stops the intel driver loading.

Be very interested to see how you get on..

---

### Post by Linuxisfast on 2012-11-04
Works fine here with Ubuntu 12.04.1 have to update after install and then install the drivers for Cedar Trail via hardware drivers. Make sure to have your net connected during installation of distro and select automatic update.

---

### Post by BicyclerBoy on 2012-11-04
Does working fine include...
Is openGL working in hardware or s/w rasterised?
Does va-api work ?
HDMI HDA audio ?
HD video modes available?

All of these are HTPC prerequisites.

---

### Post by SaltyDoug on 2012-12-31
Hi Linuxisfast,
I'm a newbe to Ubuntu (not to computers) and I have the same DN2800MT MB.  I was running the 3.2.0-29 kernel and I updated the device drivers as you stated and I saw vertical stripes on my monitor. I recently updated to the Linux 3.2.0-35 kernel and now I see vertical stripes on my monitor.  I tried nomodeset from the grub screen with the same result.   Any ideas?

Best.

---

