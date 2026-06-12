---
title: "Problem with FSC 6450g"
date: 2006-07-11
forum: Hardware &amp; Laptops
---

### Post by qkg on 2006-07-11
Hi
I'm using Ubuntu for several weeks on my desktop pc and am very happy with it. I now bought a FSC 6450g laptop and installed Dapper Drake on it.

My Problem is that I have problems with the x-server configuration, especially with changing the display resolution from 1024x798 to 1280x798. I tried to configure the xorg.conf, but without any success yet...:(
Additionally I got the newest Intel driver i810, but this didn't work out as well.

If somebody already had the same problem, I would really appreciate a post of his xorg.conf.

---

### Post by Hellkeepa on 2006-07-12
HELLo!

Please do a search for "i915 resolution", as you need to use this tool to add that resolution to the list of modes for your graphics card.
Also add the relevant resolution to the xorg.conf file, following the same syntax as the other resolutions you have available. They should all be on one line, so it's easy to find out how to do this. ;-)

Happy codin'!

---

