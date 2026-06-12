---
title: "nVidia card driver issue - can't get above 800x600"
date: 2009-05-18
forum: Hardware
---

### Post by xor.gate on 2009-05-18
Hi,

I recently installed Ubuntu 9.04, and everything was running fine out of the box. But earlier today the power went, and when I turned the computer back on suddenly my resolution was set to 640x480, and I can't seem to get it back above 800x600. It was set to 1024x768 before the power went.

I tried reinstalling the xserver-xorg-video-nv package through Synaptic, no luck. I tried uninstalling that driver and installing nVidia's driver package, that broke my xorg config (even after running nvidia-xconfig). So I restored the backed up xorg config, removed the nvidia driver and reinstalled the xserver-xorg-video-nv package. Now I'm back to square 1, except when I try starting the display app through System->Preferences->Display it tells me:

"It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?"

If I click "no" to that it starts the display tool anyways, but it's annoying having that message pop up every time.

Anybody have any suggestions?

---

