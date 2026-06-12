---
title: "monitor video issue blank screen FIXED"
date: 2008-03-11
forum: Hardware &amp; Laptops
---

### Post by firecrow8 on 2008-03-11
when I first tried to install ubunto from the cd my monitor went blank with horozontal lines then faded from white to black to white to black.  this was from the live boot cd

I then installed from the alternate cd (the checkbox at the bottom of the download page) that is a text based installer. and the install worked... and it booted up into the same blank screen.

I finally found a blog listing a solution and[B]I fixed it with

noapic nolapic
[/B]

it's a monitor/graphics card issue and ubuntu must be detecting the wrong one.

once I found the above commands and added the to the end of my boot string

(pres f6 at the ubuntu boot options screen add "noapic nolapic" without "")

it's worked fine ever since.

wanted to post this for others with the same issue

---

