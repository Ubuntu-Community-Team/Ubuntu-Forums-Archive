---
title: "Setting up applications with monitor profiles"
date: 2011-01-19
forum: Hardware
---

### Post by josvanr on 2011-01-19
hi 

I calibrated my laptop screen with dispcalgui and spyder 3 pro and
installed the resulting profile with the color management tool from 
gnome. The colors look better eg white and greys look more neutral
now. However, the colors I see are not consistent over all applications
so I'm trying to figure out how to fix this. 

In the image 
attached, you see 3 applications displaying the same image.
1) eog 2) gimp 3) display (from imagemagick). 1) is too dark, I see
no details in the shadows. 2) and 3) are ok but .. which one is it?
In gimp I chose settings: 'Color managed display' and 'No monitor
 profile'. If I choose to use the monitor profile I measured, the
image turns black like in eog. The profile was measured with gamma
set to 1.8 so the black stuff is definitely wrong (my guess)..

So any suggestions anyone? I'm about to give up on this and come
back in 5 years, see if it works then...


josvanr

---

### Post by josvanr on 2011-01-19
it looks to me as if the monitor is applied twice, once by xcalib (to the entire screen) and one in gimp (if monitor profile is chosen)?... sigh.

---

