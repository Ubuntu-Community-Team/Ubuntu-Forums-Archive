---
title: "No GLX with intel GMA965 and i915 driver"
date: 2010-12-09
forum: Hardware
---

### Post by kori.mendocino on 2010-12-09
Hello,

Basically I have no 3d acceleration ever since I upgraded to meerkat. I find this baffling, but I have been too busy with work to look into it and eventually to start asking around. The integrated graphics card is gma965. Here goes some data which should help you nice, problem-solving people:

- lspci output:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

- lsmod output:

i915                  334267  3 
drm_kms_helper         32836  1 i915
drm                   206230  3 i915,drm_kms_helper
i2c_algo_bit            6208  1 i915
intel_agp              32462  2 i915
video                  22176  1 i915

- glxinfo output:


name of display: :0.0
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual or fbconfig


Any clues, hints, tips and especially solutions are very welcome. I have searched through the forums but I have yet to find a similar problem with this distribution and graphics card.

Thanks, bye

---

### Post by HenrySpencer on 2011-10-12
no reply to this????

---

