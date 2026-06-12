---
title: "nvidia driver broken ... in a very strange way"
date: 2009-02-13
forum: Hardware
---

### Post by edgue on 2009-02-13
Hello there,

I just switched from Windows XP to ubuntu 8.10 last week; everything is quite nice; but now I am sitting in some strange trap.

Initially, our support folks installed nvidia 173 on my T61. I used jockey-kde to switch to 177 - worked out fine. Then a coworker pointed out a new 180 driver version. So I used synaptec to install that version. Again; no problem. But then I figured that with that driver, suspend to ram stopped working. OK, lets downgrad.

I used synaptec to remove 180 ... and reinstall 177.

And ever since then I am broken: whatever I try (list of things to follow) ... when i use nvidia-xconfig to enable the nvidia driver and reboot, starting X will fail:

(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!

BUT:
when I do a 
sudo insmod /lib/modules/2.6.27-11-generic/kernel/drivers/video/nvidia.ko

and startx manually ... it works.

This is what I tried:
* reinstall 180 using synaptec
* reinstall any 17x driver using jockey-kde
* delete any package with nvidia in it ... and use synaptec
to install 177, or 177, or 180

Finally I downloaded the driver installers from NVIDIA; and now ... 177 is running again on my machine.

But still it is not very convenient to not have it start the right way.

So - any idea what could be causing this problem?

many thanks

---

### Post by edgue on 2009-02-17
FYI: 
At some point I remembered that some coworker had suggested special options for the nvidia module ... that should work for the 177 driver; and that shouldnt matter for the 180 stream.

After removing all these options, my machine is happily running with the 180.29 driver ; and suspend to ram works again, too.

---

