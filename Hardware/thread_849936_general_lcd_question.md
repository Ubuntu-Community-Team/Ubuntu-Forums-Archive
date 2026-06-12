---
title: "general lcd question"
date: 2008-07-05
forum: Hardware
---

### Post by kristersaurus on 2008-07-05
Hey guys,

Recently my LCD display on my laptop started doing something odd - it no longer interpolates resolutions other than the native resolution. So when I run something less than 1024x768, it appears in a box the actual size of the resolution i am running in (for instance, during the boot process). The one exception to this is when I enter the BIOS setup..then the low resolution is stretched to fill the screen.

It made me wonder...what controls this? My laptop didn't used to do this..and I know I've seen some other machines not interpolate low resolutions...I cant find a BIOS setting and its not like there are any display drivers being loaded to control this behavior. Any ideas what would make a laptop suddenly start doing this? And how to get it back to interpolating?

---

### Post by sdennie on 2008-07-05
What graphics card are you using?  If nvidia, try running "nvidia-settings" and then going to [probably] the second to last option in the left pane and selecting the GPU scaling type.

---

