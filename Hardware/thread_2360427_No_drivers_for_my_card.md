---
title: "No drivers for my card"
date: 2017-05-04
forum: Hardware
---

### Post by erzis on 2017-05-04
Hello,
I have Radeon HD 6870 gpu. I know it is pretty old, but when I used to have windows my fps in a game were ~ 200. Now, when I have Ubuntu they cap to 60, because my drivers aren't updated. There are no drivers for my card for Ubuntu 16.04 so I use open source Ubuntu graphics card drivers which doesn't allow me to have over 60 fps. I know that linux isn't designed for gaming, but it is the only game I really play. When I open the game in window mode I get more than 120 fps. Any solutions how can I update my drivers? Do I really need to code them myself? ;c

---

### Post by QIII on 2017-05-04
Unfortunately, AMD no longer supports your GPU with a driver from 16.04 forward.  They have gone to the open source AMDGPU driver and the hybrid open-proprietary AMDGPU-PRO driver.  Neither of those supports your GPU. 

You will need to use the open source Radeon driver installed with Ubuntu, which is the one you are currently using.

Other options are to go back to 14.04.2 or earlier or to purchase a new GPU with GCN 1.0 or later architecture.

---

### Post by erzis on 2017-05-04
Ugh, I guess it is time to change distro or buy a new graphics card. Thanks for your reply. Have a nice day.

---

### Post by QIII on 2017-05-04
Changing distros will not work unless the distro has an out-dated graphics stack.  This is a "Linux thing" and not an "Ubuntu thing".

---

### Post by Yellow Pasque on 2017-05-05
> **QIII said:**
> Unfortunately, AMD no longer supports your GPU with a **proprietary** driver from 16.04 forward.

Fixed. Actually, with my personal experience with fglrx/Catalyst, I'd remove the "Unfortunately" part too...

> They have gone to the open source AMDGPU driver and the hybrid open-proprietary AMDGPU-PRO driver.  Neither of those supports your GPU.

But the radeon kernel module and the "r600g" 3D driver are already well-developed and they continue to be maintained, so I don't see how amdgpu/pro is relevant.
[http://lkml.iu.edu/hypermail/linux/kernel/1705.0/01242.html](http://lkml.iu.edu/hypermail/linux/kernel/1705.0/01242.html)
[https://cgit.freedesktop.org/mesa/mesa/log/src/gallium/drivers/r600](https://cgit.freedesktop.org/mesa/mesa/log/src/gallium/drivers/r600)

> purchase a new GPU with GCN 1.0 or later architecture.

Why? If the 6870 supports the features needed by the game(s)/app(s) and it is powerful enough to run the game, then it should work.

> Now, when I have Ubuntu they cap to 60, because my drivers aren't updated.

Are you sure it's not because vsync/TearFree is enabled? Are you actually noticing a performance issue in the game or are you just looking at the fps numbers?

---

### Post by ping-wu on 2017-05-16
> **Temüjin said:**
> Fixed. Actually, with my personal experience with fglrx/Catalyst, I'd remove the "Unfortunately" part too...

Thanks for the update.

I have heard complaints that 16.04/16.10 do not work on legacy (GCN < 1.2) AMD machines.  Both of my AMD machines belong to the new generation; the open-sourced APDGPU works great on them, but I have no way to know what's going on on the legacy machine.

What machine do you have?  Did you have problems before? Does 17.04 work on your machine?  What video driver does it use?  What about 16.04.2/16.10?

---

### Post by gordintoronto on 2017-05-17
Can you actually tell the difference between 60 fps and something faster? I thought the human eye and brain maxed out somewhere around there.

---

