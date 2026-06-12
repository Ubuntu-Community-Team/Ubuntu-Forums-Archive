---
title: "How to configure 2 AMD graphic cards in Kubuntu"
date: 2019-11-07
forum: Hardware
---

### Post by obuntu91 on 2019-11-07
Hello,
I recently moved to Kubuntu from Windows where I had 2 AMD graphic cards R9 270X and HD7870 that where managed by AMD catalyst. How can I utilize both graphic cards in Kubuntu?

Thanks for your help :KS

---

### Post by mastablasta on 2019-11-07
i am not sure it will work. this would actually be a question for AMD support.

assuming both cards use AMDGPU driver then perhaps there is a switch.
more here: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
here: [https://help.ubuntu.com/community/AMDGPU-Driver](https://help.ubuntu.com/community/AMDGPU-Driver)
and here: [https://wiki.archlinux.org/index.php/AMDGPU](https://wiki.archlinux.org/index.php/AMDGPU)

look slike AMDGPU-pro might be needed if it's supported.

> 
[LIST]
[*]**&#8203;**Supported
[LIST]
[*]APIs:
[LIST]
[*]OpenCL™1.2
[*]Vulkan™ 1.0
[*]VDPAU/VAAPI
[/LIST]
[/LIST]

[*]Basic display features
[*]Basic power management features
[LIST]
[*]Note: AMD does not perform QA validation for S4 (hibernation) function as it is highly platform dependent.
[/LIST]

[*]KMS (Kernel Mode Setting) and ADF (Atomic Display Framework) support
[*]GPL compliant kernel module
[*]AMD FirePro™ Features (EDID Management and 30-bit color) **-->> is this the feature?**
[*]FreeSync support (Please refer to this FAQ for more information)
[*]DirectGMA for OpenGL
[*]Install script and native packages for all supported operating systems
[/LIST]


---

### Post by obuntu91 on 2019-11-07
Thank you very much I'll have a look and ask AMD support

---

