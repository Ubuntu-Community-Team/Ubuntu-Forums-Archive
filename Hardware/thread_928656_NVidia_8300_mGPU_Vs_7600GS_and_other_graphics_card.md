---
title: "NVidia 8300 mGPU Vs 7600GS and other graphics cards questions"
date: 2008-09-24
forum: Hardware
---

### Post by Zaff on 2008-09-24
Hi everyone,
I use to have an MSI motherboard with an ASUS Nvidia 7600GS graphics card on the PCI Express port.
It worked very well but then I went to geek island (aka Taiwan) and brought back a new motherboard : ASUS M3N78 Pro with an integrated Nvidia 8300 mGPU.
Now looking at the numbers I thought the integrated graphics would be more performant than my old but reliable 7600GS. However, it seems it's not and I'm wondering if that's normal or if it's because I did something wrong. it looks like it's slower and some compiz effect just don't seem to work (the cube for instance).

I installed this driver for the NVIDIA 8300 : [http://www.nvidia.com/object/linux_display_ia32_173.14.12.html](http://www.nvidia.com/object/linux_display_ia32_173.14.12.html) by the way...

So first I'd like to ask if anyone can shed some light on this or experienced something similar ?

If I decide to install my old 7600 GS on the motherboard is that going to be a problem ? Will I have conflicts because there's already a graphics chipset in there ? Is there some tutorial talking about stuff like that ? Can I dual screen ?

Finally I might just decide to buy a new graphics card. Any recommendation as to what to buy ? What is better supported nowadays ATI or Nvidia ?

Thanks for all the help.

---

### Post by Zaff on 2008-09-25
hate to do that but
bump
And also I have this other weird issue : I have to reinstall the NVIDIA driver everytiem I shut down my computer. It's fine if I hibernate or suspend. But if I shut down and restart, I get the display menu where the mouse is a cross and it tells you to choose the driver.
I reinstall and everything works fine but it's annoying as hell, I think I'll go back to my old 7600GS if no one can help with that...

---

### Post by ginggs on 2008-10-13
Try using Envy NG to install the Nvidia driver.
Look for the envyng-core and envyng-gtk packages in Synaptic.

---

### Post by Zaff on 2008-10-13
found out there were some remains from previously installed nvidia package and that's why I had to reinstall everything every time. It works now thanks.

Also the 7600GS is much more performant than the integrated 8300 mGPU (for those who were wondering).

---

