---
title: "MSI CR420 hang on shutdown or restart"
date: 2011-05-21
forum: Hardware
---

### Post by iip on 2011-05-21
Hi All,

I just try to install Natty on MSI CR420 laptop, all hardware seem detected and most of them are works, but when I try to shutdown or restart, the laptop hang, it stuck on somewhere, the last line show on the screen when it stops were random.

I try with Maverick and Natty, both are the same, all stuck when trying to shutdown or restart. I have try with option nolapic noacpi the result are still the same.

Anyone experienced with this?

thanks,

-iip-

---

### Post by iip on 2011-05-26
fixed! by updating new kernel from kernel PPA, the problem were come from wireless device which is use rt2x00 modul.

---

### Post by diegoviola on 2011-06-07
it sounds like the same issue we have here:

[https://bugzilla.kernel.org/show_bug.cgi?id=33872](https://bugzilla.kernel.org/show_bug.cgi?id=33872)

---

