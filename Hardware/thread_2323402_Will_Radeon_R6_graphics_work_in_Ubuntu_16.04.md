---
title: "Will Radeon R6 graphics work in Ubuntu 16.04?"
date: 2016-05-05
forum: Hardware
---

### Post by forkandles on 2016-05-05
I am contemplating the purchase of this **HP 455** (Ubuntu 12.04 installed) laptop:

[http://www.ebuyer.com/705955-hp-455-quad-core-laptop-l8b56es](http://www.ebuyer.com/705955-hp-455-quad-core-laptop-l8b56es)

AMD A10-7300 APU 1.9GHz with Radeon R6 Graphics featuring 10 Compute Cores (4 CPU + 6 GPU).

I intend to use Ubuntu 16.04, but I read that there **may** be a problem **using Radeon R6 graphics in 16.04**:

[http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04](http://www.omgubuntu.co.uk/2016/03/ubuntu-drops-amd-catalyst-fglrx-driver-16-04)

Can anybody offer any advice please?

I want the **R6 graphics** to function properly, so I do not want to buy a dud.

I know that I can use another distro but I happen to like Ubuntu 16.04, which I use on another machine.

---

### Post by mastablasta on 2016-05-05
it is supported by AMDGPU driver which is still under development. if you need all functions offered by fglrx you should use 14.04 or 15.10 (until amdgpu get's better).

you should check phoronix for any news and to see if amdgpu is already on par with fglrx or not.

chip is probably supported by radeon opensource drivers as well, however they perform about 20-30% worse than fglrx.

---

### Post by forkandles on 2016-05-05
mastablasta,

Thanks for the reply.

I will probably use Ubuntu 14.04 in the meanwhile and then decide what to do in 2019.

---

