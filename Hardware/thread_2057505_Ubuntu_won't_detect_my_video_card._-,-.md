---
title: "Ubuntu won't detect my video card. -,-"
date: 2012-09-13
forum: Hardware
---

### Post by vanillasnow on 2012-09-13
This is the video card I have:
[http://www.amazon.com/dp/B00861BB0S/...hvptwo=&hvqmt=](http://www.amazon.com/dp/B00861BB0S/...hvptwo=&hvqmt=)

When I go to system details it gives me all but the graphics information. I get the CPU info, RAM info etc. 

Anyone have an idea of how I can solve this? Your feedback is appreciated. 

I've tried installing it manually via terminal,but no matter how many methods I try; I always end up with "aticonfig: No supported adapters detected."

Your feedback is appreciated. =)

---

### Post by papibe on 2012-09-13
Hi vanillasnow

Could you post the result of this command?
```
lspci -nnk | grep -iA3 vga
```
Regards.

---

