---
title: "Are there any improvements on Intel 82945G/GZ Integrated Graphics Controller?"
date: 2009-03-19
forum: Hardware
---

### Post by ivanvajar on 2009-03-19
:-) As I asked: Are there any improvements on Intel 82945G/GZ Integrated Graphics Controller? I was unable to get Compiz to work on this chip. Does anyone know what is happening with it?

---

### Post by thtrgremlin on 2009-03-19
I looked up this page: [http://support.intel.com/support/graphics/intel945g/](http://support.intel.com/support/graphics/intel945g/)

It appears according to product data that the card does support 3d. However, in my experience, the Linux driver support for 3D on Intel cards is limited. On the FAQ for the page it shows quite a few known issues with 3D support for Windows, especially when using Vista. If the Intel drivers are having as many problems as it describes, I am not necessarily surprised that such issues would also manifest themselves when trying to use compiz.

That being said, the best place to check easily is in jockey (System->Administration->Hardware Drivers) for a proprietary driver. Typically if a new driver becomes available as part of an update a notification icon will appear letting you know.

If you are feeling bold and are pretty familiar with things, you may wish to try an Ubuntu Jaunty Jackalope Alpha CD. I DO NOT recommend upgrading just yet, but if you download the iso and test it out in a live session you can get a preview of what the support will most likely be at the end of April with the new version. 9.04 is in code freeze, so if something new is going to be included, it is included now.

Hope that gives you some direction. Best luck.

---

