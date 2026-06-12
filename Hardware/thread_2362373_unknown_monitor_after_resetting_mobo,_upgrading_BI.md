---
title: "unknown monitor after resetting mobo, upgrading BIOS"
date: 2017-05-27
forum: Hardware
---

### Post by ubuntini2 on 2017-05-27
Solving one issue(CPU fan error on boot) I've created another.

I reset my mobo completely to defaults as well as upgraded my BIOS.

But know when I boot into ubuntu my monitor isn't recognized.

Only see default resolution of 1024x768 and unknown monitor.

Should see default resolution of 2560 x 1440 pixel on my Dell 27".

---

### Post by Autodave on 2017-05-28
Did Ubuntu ever recognize the correct resolution?  How are you connecting thew monitor to the PC: VGA, DVI, HDMI, ??.

---

### Post by ubuntini2 on 2017-05-30
Op. Issue was I forgot to disable Secure Boot in my BIOS-UEFI. I think something about not being able to load 3rd party drivers, Nvidia in this case.

---

