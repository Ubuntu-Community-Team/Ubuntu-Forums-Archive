---
title: "Confusion on video driver being used"
date: 2012-10-04
forum: Hardware
---

### Post by ventikappa on 2012-10-04
I'm running Precise 12.04 on an Acer AspireOne 751h netbook (i.e. with Atom and GMA500 adapter).
According to 'System Setting-Details-Graphics' it seems that  Gallium 0.4 on llvmpipe as video driver.
(I did not install Gallium deliberately. I suspect it happened upon installing mesa-utils in order to solve the problem of the "Unknown Driver" message in 'System Setting-Details-Graphics' as suggested [here]("http://ubuntuforums.org/showthread.php?t=2002678").
However, if I do 'lsmod' I'm getting "psb_gfx" for the video.
As indicated in other posts (e.g. [here]("http://ubuntuforums.org/showthread.php?t=2039705&page=3")) Atom processor can hardly cope with the processing implied by Gallium, so I'd like to get rid of it and move back to psb_gfx. I know that by doing this I'm giving up 3D support, but I don't really mind (in the end, if the machine becomes unusable I'm not getting 3D anyway...).
I've found posts that tell how to blacklist Gallium, but I'd like to make sure I don't end up having no driver loaded at all.
On the contrary, if Gallium is not being used in reality, is that message in 'System Setting' just wrong or am I rather mixing things up?
Thanks!
 - Carlo

---

