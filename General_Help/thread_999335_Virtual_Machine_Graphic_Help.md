---
title: "Virtual Machine Graphic Help"
date: 2008-12-01
forum: General Help
---

### Post by DeeXener on 2008-12-01
I have Ubuntu installed on VirtualBox under Vista. It runs fine and I really like this setup. I'm really stuck on getting the effects in Ubuntu to work. When I try to enable them it says it just can't. My graphic drivers are generics that came with VirtualBox and I'm mentioning that because that might be the issue. I have a ATI Radeon HD 3450 with 128MB. If someone could point me to some drivers and how to install them that would be great.

Many thanks!

---

### Post by Trueno22 on 2008-12-01
What effects are you talking about?  The Vista ones?  To install video drivers in Virtualbox add this to /etc/X11/xorg.conf:

> Section "Device"
	Identifier	"Configured Video Device"
	Driver		"vboxvideo"
EndSection

Then restart X. The next time you run Virtualbox it will automatically install the drivers.  Be sure to change the video settings to use 128Mb of Graphics RAM.

---

### Post by binbash on 2008-12-01
If you are talking about compiz fusion effects, forget it

---

### Post by DeeXener on 2008-12-01
> **binbash said:**
> If you are talking about compiz fusion effects, forget it

Pray explain?

---

### Post by binbash on 2008-12-01
THere is no 3d support at virtual box, how can you use 3d effects?

---

### Post by DeeXener on 2008-12-01
I did not know that. Hmm.. Well thanks for educating me on that. 
It does suck, but it isn't too much of an issue.

---

### Post by binbash on 2008-12-01
Vmware has a limited 3d support, you may try it but i do not suggest.

---

### Post by obsrv on 2008-12-23
I set vboxvideo in xorg.conf but it says there is no such module. what I need to install? I cannot install VBoxGuestAddtions.iso because I need something with the kernel. I tried installing virtualbox-ose-guest-modules but didn't helped. Im stuck in 800x600 and I need 1280x720. I have defined these resolutions in xorg.conf

---

