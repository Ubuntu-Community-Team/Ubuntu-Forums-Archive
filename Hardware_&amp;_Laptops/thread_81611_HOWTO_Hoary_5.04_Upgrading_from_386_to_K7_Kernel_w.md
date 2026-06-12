---
title: "HOWTO: Hoary 5.04 Upgrading from 386 to K7 Kernel with Nvidia card"
date: 2005-10-24
forum: Hardware &amp; Laptops
---

### Post by KeithUK on 2005-10-24
Just worked out how to fix something and thought I'd feed it back.

Here's the scenario:

I have an AMD Athlon based box with an NVIDIA TNT2 Model 64/Model 64 Pro graphics card.

I have Ubuntu Hoary Hedgehog 5.04 installed with the native Nvidia drivers. Everything worked a treat, no problems.

I recently read that the base install of Ubuntu is for a 386 kernel but that there is a specific K7 kernel which should give better performance.

I checked with Synaptic and sure enough I had 'linux-image-2.6.10-5-386' installed.

OK. no problem I thought, so I found 'linux-image-2.6.10-5-k7' and installed that as well.

At the next reboot I started the K7 kernel (GRUB default now) and the native Nvidia driver crashed and the Xorg GUI failed to start.

I did a search of the forums and found a lot of stuff about legacy drivers for older cards and wasted a lot of time and effort farting around with them. 

DON'T DO IT it's a rat hole and isn't the problem!! 

You don't need to legacy drivers you just need to install the K7 versions of the Nvidia drivers for the K7 kernel you've just installed.

To get back to the GUI is no problem because you still have the 386 option in the GRUB menu.

Once you've restarted with the 386 kernel and got the GUI working, start up Synaptic and install 'linux-restricted-modules-2.6.10-5-k7'.

Reboot and select the K7 kernel from GRUB (should be the default) and voila, a K7 kernel with native Nvidia drivers.

Hope this helps someone out there :)

And yes, the new kernel does make a difference, not a lot but still noticable, especially to the Xorg GUI speed.

(yes, yes, I know I should be moving to Breezy Badger instead of mucking around with Hoary Hedgehog. I will as soon as the CDs arrive - I'm on dial up)

Regards,

Keith Watson

---

### Post by Gr33dy on 2005-10-27
Hey thanks works great.
all i needed to complete my k7 kernel install :) :)

P.S. i dont think ill install 5.10 because 5.04 is rock solid, everything works and i dont use openoffice and i dont see the need to fix something thats not broken.
thanks again....

regards Gr33dy

---

