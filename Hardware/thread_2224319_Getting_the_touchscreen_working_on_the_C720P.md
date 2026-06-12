---
title: "Getting the touchscreen working on the C720P"
date: 2014-05-15
forum: Hardware
---

### Post by troy8 on 2014-05-15
To anyone that's trying to get the touchscreen working correctly, here is a tip.  Build "mxt-app" from Atmel [https://github.com/atmel-maxtouch/obp-utils](https://github.com/atmel-maxtouch/obp-utils) and flash '1664s_RAW' (google it).  I think with a 'RAW' dump from a working C720 you can probably get the touchpad working the same way.  Once you flash it, you won't need most of those crazy xorg.conf file settings.  Most of those are in the 'RAW' file.  That is the way Google does it.

---

### Post by Bao_Niu on 2014-06-05
Hi Troy8,
Thank you very much for your post, it is very needed.
I am running Ubuntu 14.04 64-Bit on my acer c720P chromebook. I don't have much experience in scripting nor ubuntu hacking, so something related to "compiling" is really scary to me. Your post is very tempting but a little bit over my head for me to understand. For example, I found those RAW files online but still don't know where to start. Could you please give a more newbie-friendly walk-through on how I can setup my touch-pad and touch-screen from a freshly installed ubuntu 14.04?

Many thanks.

---

