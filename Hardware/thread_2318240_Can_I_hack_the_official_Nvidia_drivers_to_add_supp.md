---
title: "Can I hack the official Nvidia drivers to add support for my legacy GPU?"
date: 2016-03-24
forum: Hardware
---

### Post by Brinstar on 2016-03-24
I have a Nvidia 310M and support was removed in the latest beta drivers

[http://www.nvidia.com/download/driverResults.aspx/100577/en-us](http://www.nvidia.com/download/driverResults.aspx/100577/en-us)

It's unfortunate because these were the first drivers to add Mir and Wayland support, so is there any way to modify the installer to support my GPU?

---

### Post by oldfred on 2016-03-24
If you go to this page, it shows the supported driver.
[http://www.geforce.com/drivers](http://www.geforce.com/drivers)

Yours is now frozen at 340.xx. Updates are only for security or fixes. Note below looks like until April 2016 the 340.xx driver would get updates.

The newest drivers are designed to support all the new features of newer cards that are not in your card anyway.
Also a way for nVidia to get users to upgrade to new card/computer.

At least nVidia keeps a working frozen driver for just about every older model card/chip. And the Ubuntu repository has all those old drivers to use if you have an older card.

 NVIDIA is ceasing to support their older GeForce 8, 9, 200, and 300 series from their mainline driver but the NVIDIA 340.xx driver series will become a long-term legacy driver that they will commit to supporting until April of 2016. 
[http://nvidia.custhelp.com/app/answers/detail/a_id/3473](http://nvidia.custhelp.com/app/answers/detail/a_id/3473)
[http://nvidia.custhelp.com/app/answers/detail/a_id/3142/session/L2F2LzEvdGltZS8xNDAyMzMzMDI0L3NpZC9fVTZwRW9XbA%3D%3D](http://nvidia.custhelp.com/app/answers/detail/a_id/3142/session/L2F2LzEvdGltZS8xNDAyMzMzMDI0L3NpZC9fVTZwRW9XbA%3D%3D)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by Brinstar on 2016-03-24
> **oldfred said:**
> 
The newest drivers are designed to support all the new features of newer cards that are not in your card anyway.
Also a way for nVidia to get users to upgrade to new card/computer.


I think we all realize that. A 310M could easily render a desktop through Mir/Wayland, so those new features you mentioned don't really come into this. 
I know its forced obsolescence, but it occurred to me there must be a way to enable the newer drivers on older hardware. Unofficially, of course.

---

