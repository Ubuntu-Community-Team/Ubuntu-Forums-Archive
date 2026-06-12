---
title: "Weird Xorg problems w/ external CRT?!"
date: 2006-11-08
forum: Hardware &amp; Laptops
---

### Post by roots on 2006-11-08
hi,

i got the following setup:

acer travelmate tmi382 (12" 1024x768)
samsung syncmaster 940B
ubuntu dapper drake

i want to use either internal or external screen. the external screen is recognized but runs in 1024x768 only! i've been trying to get it working with 1280x1024 for quite some hours, but what Xorg.0.log tells me is:

```

(II) I810(0): Generic Monitor: Using hsync range of 28.00-51.00 kHz
(II) I810(0): Generic Monitor: Using vrefresh range of 43.00-60.00 Hz
(II) I810(0): Not using built-in mode "1280x1024" (width too large for virtual size)
(--) I810(0): Virtual size is 1024x768 (pitch 1024)
(**) I810(0): *Built-in mode "1024x768"
(**) I810(0): *Built-in mode "800x600"
(**) I810(0): *Built-in mode "640x480"
(II) I810(0): Attempting to use 60.00Hz refresh for mode "1024x768" (854)
(II) I810(0): Attempting to use 60.32Hz refresh for mode "800x600" (852)
(II) I810(0): Attempting to use 60.00Hz refresh for mode "640x480" (850)
(==) I810(0): DPI set to (75, 75)

```

anyone knows how to solve this?


cheers,
roots.

---

