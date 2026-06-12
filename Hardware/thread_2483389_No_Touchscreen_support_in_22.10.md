---
title: "No Touchscreen support in 22.10"
date: 2023-01-29
forum: Hardware
---

### Post by tomas-serret on 2023-01-29
I recently bought a Huawei Mate book X Pro 2022 and the touchscreen is not supported, meanwhile in 22.04 it is and it works fine. Workaround, to edit grub with gksu will not run, gksu is mot supported any longer. Please enable touchscreen functionality in further releases of ubuntu and fix this Prob.

Many thx

I tried this workaround 
[URL="https://www.reddit.com/user/lecano_/"]

[/URL]

nivel 1[lecano_]("https://www.reddit.com/user/lecano_/")


 · [hace 4 m]("https://www.reddit.com/r/archlinux/comments/ym59lo/comment/iv1xuy1/?utm_source=reddit&utm_medium=web2x&context=3")

[https://wiki.archlinux.org/title/Intel_graphics#Screen_flickering](https://wiki.archlinux.org/title/Intel_graphics#Screen_flickering)





[COLOR=#1A1A1B]20[/COLOR]



[I][I]nivel 2[-cr4sh-]("https://www.reddit.com/user/-cr4sh-/")


[COLOR=#0079D3]PO[/COLOR] · [hace 4 m]("https://www.reddit.com/r/archlinux/comments/ym59lo/comment/iv22hqc/?utm_source=reddit&utm_medium=web2x&context=3")

I have the same issue with the 4.8 kernels. Seems it&#8217;s upstream.
After a lot of Googling I found a workaround for Intel (i915)
open  terminal gksudo gedit /etc/default/grub edit line  GRUB_CMDLINE_LINUX_DEFAULT="quiet splash&#8221; add i915.enable_psr=0 in the  quotes e,g. GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.enable_psr=0&#8221;  save sudo update-grub reboot

Fixed!! Thx so much!



[/I][/I]
IT DIDN'T WORK for me. I edited grub with nano, sudo gedit didn't work on 22.10. Then I tried to install on 22.04 the jammy proposed actualizations under Development and the same error happened again. For me it looks like that only the LTS will have full screen support or Cannonical will introduce the future versions with limited screen support. 

Can anybody help or tell me about Cannonicals plans?

THX again

---

