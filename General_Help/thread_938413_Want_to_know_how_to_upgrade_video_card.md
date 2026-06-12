---
title: "Want to know how to upgrade video card"
date: 2008-10-04
forum: General Help
---

### Post by rhomp2002 on 2008-10-04
I am replacing the IGP on my MoBo with the ASUS EN9600GT TOP video card.  My question is how do I install the card and drivers.

The reason I am asking is that some distros want you to install the card and then log in.  The assumption is that the distro will recognize the card and install the proper drivers.  Other distros want you to install the driver, then install the card and then log in.  At that point you can then fix up the resolution, etc.

I have both Ubuntu and Kubuntu.  Which way do I do it for these two distros.:confused::confused:

---

### Post by elmer_42 on 2008-10-04
While I have personally not upgraded a video card between distros, I believe that even if it does not find the correct driver for the GPU, you can use VESA until you can get the driver installed. I would upgrade the card, plug your monitor into it, set your default output to PCIe in your BIOS, and then boot up. You can then install the driver.

I used a similar method with my current PC. It uses an nVidia 7600GT, and it was detected flawlessly by Ubuntu 7.10. I hope you have as much luck as I did.

---

