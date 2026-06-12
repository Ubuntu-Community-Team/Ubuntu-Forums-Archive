---
title: "75hz option in nvidia-settings does nothing"
date: 2009-06-15
forum: Hardware
---

### Post by PurposeOfReason on 2009-06-15
I was able to get a 75hz option for my monitor in nvidia settings by adding a modeline to my xorg.conf. It was generated using powerstip under windows where 1680x1050@75hz is working. But under linux, it defaults to 60hz, with an option in nvidia-settings for 75hz which is selected by default. It doesn't do anything though, still reporting at 60hz.

If I bring up xvidtune, all the timings are set for 75hz, but if I click apply I get "Sorry: You have requested a mode-line that is not possibe . . .". Obviously, since these timings worked in Vista, they are indeed possible.

---

