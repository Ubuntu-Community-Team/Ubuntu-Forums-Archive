---
title: "Is i915 the latest driver?"
date: 2009-12-10
forum: Hardware
---

### Post by daromansky on 2009-12-10
Hi,

I am not new to Linux at all, but I cant figure out if I am running the correct driver for my video card.

This is the relevant line from lspci:
[FONT=monospace]00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

I am running on Lenovo x200s, which is using the Intel x4500HD (or similar named) IGC.

BUT, in lsmod I can see that I am using a driver called "i915", - this is the reason I opened this thread, it sounds old to me =q

Should I be seeing different driver name than "i915" ??

Cheers!
-- Roman
[/FONT]

---

### Post by HappyFeet on 2009-12-10
See [this]("http://www.intel.com/support/chipsets/sb/CS-025753.htm").

---

### Post by daromansky on 2009-12-11
Gee what a short and irrelevant question, did you even bother reading?

> **HappyFeet said:**
> See [this]("http://www.intel.com/support/chipsets/sb/CS-025753.htm").


I was asking about the name of the driver "i915", I have the latest one installed from the repo, I am not sure if the one used (in lsmod) is the correct one.

---

