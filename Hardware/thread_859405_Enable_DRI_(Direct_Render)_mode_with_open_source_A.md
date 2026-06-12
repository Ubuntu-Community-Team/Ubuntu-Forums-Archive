---
title: "Enable DRI (Direct Render) mode with open source ATI driver"
date: 2008-07-14
forum: Hardware
---

### Post by Harry Muscle on 2008-07-14
I tried following the instructions provided here:
[https://wiki.ubuntu.com/X/RadeonXpress](https://wiki.ubuntu.com/X/RadeonXpress)
to enable Direct Rendering (DRI) mode on my Xpress 1150 graphics card.  I've read about other people being able to do it following those or similar instructions, but for some reason I can't.

On Ubuntu Hardy is enabling DRI on the open source drivers as simple as adding the DRI true option to the xorg.conf file plus the mode setting for DRI?  Or is there something I need to do that's obvious, but not mentioned in the above link that I'm missing.

Is there anything special that needs to be added to the xorg.conf file, like which modules to load?  What about specifying which driver to use?  I've tried specifying both ati and radeon and both still gave me a NO when I check if direct rendering is enabled.

Any help you can offer is highly appreciated.

Thanks,
Harry

---

### Post by markbuntu on 2008-07-14
The 1100 xpress series is supported by the ATI restricted driver so perhaps you would be better off with that for your DRI needs.

---

### Post by Harry Muscle on 2008-07-15
> **markbuntu said:**
> The 1100 xpress series is supported by the ATI restricted driver so perhaps you would be better off with that for your DRI needs.

Unfortunately the restricted ATI driver doesn't support 1280x720 resolution which I need.  The open source driver has no issues with this resolution, I just can't get DRI to work (on any resolution) with the open source driver.

Thanks,
Harry

---

