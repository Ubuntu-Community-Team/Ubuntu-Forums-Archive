---
title: "TV Out, help required please."
date: 2008-01-22
forum: Hardware &amp; Laptops
---

### Post by clpc on 2008-01-22
I have an nVidia GEForce 6800 GS 512MB and as a spare a 7300 GS 128MB
I currently have the 6800 installed but the problem I have is the same with both cards.

I am running Gutsy.
I have the nvidia-glx-new drivers installed and in use i.e. driver=nvidia not nv
So all the flashy desktop effects work fine but I don't like them so I have all the flashy effects turned off.

I have spent days trying to get my TV-OUT on the nvidia card working, I am no further forward than I was when I started.
nvtv reports...
Fatal: No supported video card found.

nvidia-settings will not detect any displays and under the 'Configure' only the 'Seperate X Screen' is enabled, so I cannot select TwinView. If I enable TwinView in xorg.conf it is ignored.

The relevant line from lspci is....
05:00.0 VGA compatible controller: nVidia Corporation NV41 [GeForce 6800 GS] (rev a2)

I have tried just about every combination for my xorg.conf that I can find, I have followed numerous how-to's and suggestions.

I think I must be missing something rather fundamental, as it appears that the OS thinks I have a house brick instead of a video card.

Can anyone please help?

---

