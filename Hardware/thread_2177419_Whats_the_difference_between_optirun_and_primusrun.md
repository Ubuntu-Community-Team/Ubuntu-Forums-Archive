---
title: "Whats the difference between optirun and primusrun?"
date: 2013-09-28
forum: Hardware
---

### Post by junglejuice on 2013-09-28
hi,
I'm using 12.04.2 x64 with bumblebee, on a lenovo y580 with intel graphics and a geforce 660m. Everything seems to be working perfectly with regards to graphics rendering and switching between gpu and dgpu. I generally only use my nvidia card in blender by innitialising it with the primusrun command, as expected blender detects my card and switches to CUDA as it's compute device. starting blender with the optirun command yields the exacting results. rendering in blender using optirun or primusrun yields almost exacting times for the same scene, with maybe 21/100th of a second's difference (and this is more than likely related to other factors).
the strange thing is that when i run glxspheres with optirun i get about 179fps but when i run it with primusrun the results are almost identical to running it with my intel card i.e. about 59fps (this is despite the terminal output noting that the geforce card is being used for rendering).
so I'd like to know when am i supposed to use optirun and when am i supposed to use primusrun, and wut are the differences as the bumble bee wikki doesn't seem to make mention of the latter?
thanks, if u can help

---

