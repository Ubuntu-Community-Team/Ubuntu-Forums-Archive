---
title: "bcm4318 led shuts off/on at times while loggin in"
date: 2009-07-12
forum: Hardware
---

### Post by acimmarusti on 2009-07-12
Hi there,

My laptop has a broadcom 4318 chip based device. Network manager seems to behave well for me using Debian Lenny, but sometimes (and this happens randomly) it won't connect automatically so I have to do it manually. This, however, is correlated to the fact that my wireless LED turns suddenly off (also random) after logging in. I was thinking it was not Network Manager's fault, but my kernel configuration that allows shutting on/off my wireless without the need to restart using the button....do you know how to prevent this from happening by any chance?
I remember not having this issue when I was on ubuntu 8.10, 8.04 nor OpenSuSe 11.1. I keep thinking it's the rfkill_input module, but I'm not sure. Is this module loaded by default in Ubuntu...if it's not, I could blacklist it and hope this will fix it.

Thanks for the help!

---

