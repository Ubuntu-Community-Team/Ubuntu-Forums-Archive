---
title: "Crazy colours!"
date: 2007-04-11
forum: Hardware &amp; Laptops
---

### Post by sprocket1985 on 2007-04-11
Since around the time that feisty herd 4 was released, I've been having problems with nvidia drivers in both feisty and edgy (and also in windows actually):
In windows, the driver causes random crashes (no BSOD, just resets) and 3d applications show blackscreens during manipulation. I include this only for full information, since I hate using windows. As an amusing side note, a 3d design application I use in windows for my degree is only usable running in windows emulated in vmware inside linux lol.
In linux:
With the 877x driver, X crashes when it starts.
Using the 9755 driver, I get a black screen as the login screen appears. This can be rectified by switching display (Ctrl+Alt+F#) and back again.
Using the 96xx driver (adept reverted to it today in the update), I get a screen full of crazy flashing colours. This can be rectified in the same way as above.
This wouldn't be a problem (a minor inconvenience at best), but an additional effect is that opengl applications (e.g. screensavers and glxgears) do not work, and aiglx/beryl/compiz refuse to work even using the xconf backup that worked before the problems started (frustrating).
Does anyone have any idea what is going on? Better still, does anyone have any idea how to fix it? Is my graphics card approaching silicon heaven?

Kernel: 2.6.20-14-generic, and whatever the latest edgy x86 one is
Architecture: tried both x86 and x86_64 on feisty
Graphics core: NVIDIA 6800 Ultra 128MB
Drivers tried: 8774, 8776, 9629, 9631, 9646(?), 9755 (have tried both binary from nvidia and the repository where possible)

---

### Post by renzokuken on 2007-04-11
definately a hardware problem.

it may be something as simple as the card became slightly dislodged/loose in its PCIe/AGP slot

open your pc, remove the card and put it back in. see if that does anything

---

### Post by sprocket1985 on 2007-04-11
okay i'll give it a try later. thanks a lot

---

### Post by sprocket1985 on 2007-04-11
I feel like such an idiot for not that myself lol.
Problem solved; I don't think I've ever been so pleased to see the nvidia boot splash :)
Thankyou renzokuken, you truly are a god

---

