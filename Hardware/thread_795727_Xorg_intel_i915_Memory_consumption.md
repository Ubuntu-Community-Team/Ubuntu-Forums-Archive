---
title: "Xorg intel i915 Memory consumption"
date: 2008-05-15
forum: Hardware
---

### Post by thornelawler on 2008-05-15
Hi folks,

I have been running Gutsy on my Thinkpad T43 (intel i915 graphics, 512MB of RAM) for a while now, and all was well, but since I upgraded to Hardy, my Xorg memory footprint has ballooned to about 400MB at startup, making it very difficult to do anything at all. 

I can see in /var/log/Xorg.0.log that it's allocating 256MB of shared memory.

I have tried the VideoRam setting, only to find that it appears to have been disabled *to decrease memory usage*.

I have tried disabling dbe, dri, glx and vbe, and the overall footprint has dropped to about 300MB, but Xorg is still allocating 256MB of shared memory.

How can I restrict Xorg (intel) to use less shared memory?

---

