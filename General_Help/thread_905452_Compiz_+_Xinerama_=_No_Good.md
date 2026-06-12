---
title: "Compiz + Xinerama = No Good?"
date: 2008-08-30
forum: General Help
---

### Post by FlintyVamp on 2008-08-30
Hey,

I'm running an nVidia 7800GT and I'm trying to get Compiz to enable when I run dual monitors but I get the error 

"The Composite extension is not available".

I know it can work as I did it the other day but just can't remember how.

It's driving me crazy. Any ideas?

Cheers,

---

### Post by gus_393 on 2008-09-14
I`m having the same problem. This is quite obviously xinerama related since when I disable it I appear to be good to go.

I have an NVIDIA card. Is there perhaps a way to use twinview with compiz instead? What are our options here if we cant give up the dual screen.

Thanks for any help guys.

oh I should also say that I have searched the forum extensively and this doesnt appear to be addressed. Any mixture of the commands below in ones xorg.conf have no effect:

Section "Device"
Identifier "nVidia Corporation MCP51 PCI-X GeForce Go 6100"
Driver "nvidia"
Option "AddARGBGLXVisuals" "True"
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "True"
Option "backingstore" "True"
Option "TripleBuffer" "True"
Option "DisableGLXRootClipping" "True"
EndSection

and at the end

Section "Extensions"
Option "Composite" "Enable"
EndSection

---

