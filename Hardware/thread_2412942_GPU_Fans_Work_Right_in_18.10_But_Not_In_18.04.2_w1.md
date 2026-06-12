---
title: "GPU Fans Work Right in 18.10 But Not In 18.04.2 w/18.10 HWE Stack.  Why?"
date: 2019-02-19
forum: Hardware
---

### Post by lostmoonofsaturn on 2019-02-19
The video card here is an AMD Radeon Vega 64.  The fans are designed not to run until the GPU temperature exceeds 60C.

This works correctly using 18.10.

This does not work correctly in 18.04.2. The Vega 64 fans are always running.

I've seen this behavior in 18.04 since its release.  I'd hoped that with 18.04.2 moving to the HWE using the 18.10 kernel and Mesa stack that the fans would function correctly.

I'd very much like to know what accounts for this difference in behavior and how to get the fans to function correctly in 18.04.2.

---

### Post by nicholasarussell on 2019-02-21
Which drivers where you using before? does switching back resolve the issue?

If it does it could be an issue in the latest driver pack :) 

Sometimes the hardest problems can have the simplest solution :) 

Kind regards,

---

