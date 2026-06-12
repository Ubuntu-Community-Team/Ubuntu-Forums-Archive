---
title: "Brightness on Lenovo B51 Amd R5 M330 running Ubuntu 16.04"
date: 2016-04-23
forum: Hardware
---

### Post by ckrles on 2016-04-23
Hi. I have a Lenovo B51 with a i5 CPU but also an Amd R5 M330. Brightness keys work well and out of the box but the settings are not save. If I set the brightness to the lowest it goes up to its highest on every reboot.

Am I missing a driver? any solution?

Thank you very much.

Edit: I don't know how but, after my last try, I did nothing else and now brightness settings are saved. However, I seem to be using Intel's Graphics instead of Amd. How can I use the amd GPU which I guess would be more powerful than Intel's?

Thanks again.

---

### Post by ntomka on 2016-04-26
I have almost the same configuration and I found out that R5 M330 not yet supported by both proprietary and open source drivers. So we have to live with the intel gpu for a while.

---

### Post by ckrles on 2016-04-28
> **ntomka said:**
> I have almost the same configuration and I found out that R5 M330 not yet supported by both proprietary and open source drivers. So we have to live with the intel gpu for a while.

Any idea about when we'll have he driver?

I read that someone used the M230 drivers successfully  [http://askubuntu.com/questions/712259/amd-graphics-card-driver-for-r5-m330](http://askubuntu.com/questions/712259/amd-graphics-card-driver-for-r5-m330) Anyone has tried?

Before messing up my system, I'd like to know other users' experiences with the M230 driver.

Thanks

---

### Post by ntomka on 2016-05-24
> Any idea about when we'll have he driver?

I don't know. Maybe amdgpu opensource driver will support it at least next year, or maybe in 16.10 later this year.

> I read that someone used the M230 drivers successfully

Yes, catalyst drivers (fglrx) works in ubuntu 15.10 out-of-the-box, and they are in the official repos. I tried it. But since ubuntu 16.04 catalyst driver are not supported anymore.

---

