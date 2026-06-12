---
title: "Brightness keys don't work with ACPI enabled"
date: 2008-04-14
forum: Hardware &amp; Laptops
---

### Post by jimv on 2008-04-14
Ok, here's what's happening.  I have a Gateway MT3418 laptop.  My brightness keys have not worked at all in 7.0, 7.10, and 8.04 unless I boot up with ACPI disabled...which I do not want to do, because then my volume and sleep keys don't work.

Here's my question:  why would disabling ACPI allow the brightness keys to start working?  Is it possible that ACPI is intercepting the brightness key strokes instead of some other process that supposed to be getting them?  Is there a way to modify ACPI to not do that? 

I'm just guessing here...what do you guys think?

---

### Post by Gen2ly on 2008-04-14
I detailed how to manually adjust AcPI eariler in this post:

[http://ubuntuforums.org/showthread.php?t=755052](http://ubuntuforums.org/showthread.php?t=755052)

Does this help? or is AcPi not responding still.

---

### Post by jimv on 2008-04-21
"Does this help? or is AcPi not responding still."

I don't actually have anything showing up under /proc/acpi/video.

---

