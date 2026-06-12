---
title: "Nvidia FX5200 and resolution problem"
date: 2012-12-23
forum: Hardware
---

### Post by colt2x on 2012-12-23
My old computer is used by my mother now. I have installed Lubuntu 12.04 on it (on 2012.11.02), replacing the old, but perfectly working Lubuntu 11.04. After installing 12.04, it was OK for a while, but after a time, i think, there were some software updates, and resolution fall back to 640x480. I have tried many fixes.

- open source nvidia driver (nouveau, nvidia-96, experimental 310)

- previous version of nvidia driver...

- edit xorg.conf (the best result was that i copied the existing xorg.conf from my desktop computer, and with it, there is a 1280x1024 resolution, which still not fits to this widescreen monitor :D )

But no success.

The VGA card is a FX5200, which is supported by Nvidia 173 driver... But if it is supported, why is maximum resolution 640x480 with it? (I noticed, too, that my monitor is also unknown by the system.)

Strange problem, too : the nvidia-settings is now reporting that the nvidia driver is too old, and he can't use it, even if there is the latest nvidia driver installed. But i think if the nvidia-settings can start, it can generate the correct xorg.conf .

I can agree with the open source driver, this computer is not used for gaming, or such things. So i only want a resolution, fitting to the widescreen monitor (1280x768, 1280x720, or 1440x900).

Can anyone help to tell me how to set the proper resolution, on this VGA card and monitor? :S

Thanks :)

---

### Post by diskmaster23 on 2012-12-26
Can you give us a print out of your dmesg and xorg.0.log?

---

### Post by colt2x on 2012-12-27
> **diskmaster23 said:**
> Can you give us a print out of your dmesg and xorg.0.log?

Hi, 

My problem is solved by kicking off "Metamodes" option, using "Mode", and generating Modelines, in xorg.conf.

Thanks for help!

---

