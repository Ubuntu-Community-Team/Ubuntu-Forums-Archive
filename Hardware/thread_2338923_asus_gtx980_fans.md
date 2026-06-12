---
title: "asus gtx980 fans"
date: 2016-10-03
forum: Hardware
---

### Post by lik2 on 2016-10-03
My asus gtx 980 graphics card fans run very loud, I am running ubuntu version 16.04lts and in graphics it says "Gallium 0.4 on llvmpipe (LLVM 3.8, 256 bits)". I really need to find a way to lower the fan speed on my gtx 980. Thank you.

---

### Post by deadflowr on 2016-10-03
Open the Program "Software and Updates"
Go to the section Additional Drivers.
Preview the available drivers and select one.
And then click Apply and let it install the driver.
Then reboot.
Looking at nividia driver support page: [http://www.nvidia.com/Download/driverResults.aspx/77844/en-us]("http://www.nvidia.com/Download/driverResults.aspx/77844/en-us")

Your card should have support for the 343 driver and up, so nvidia-346 and higher should work.

llvmpipe means your CPU is doing the heavy lifting, fwiw.

Hope it helps.

---

