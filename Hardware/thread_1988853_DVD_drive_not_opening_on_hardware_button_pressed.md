---
title: "DVD drive not opening on hardware button pressed"
date: 2012-05-28
forum: Hardware
---

### Post by jhinbo on 2012-05-28
Hi everyone,

I know I'm not the only one having the problem stated above and I know I can most of the times (sometimes even that doesn't work) open the drive in software, e.g. by doing right-click -> eject in Nautilus.

However, I really find this to be annoying - if I press a button on a device, I want the device to react to my action! Question: Is this a desired feature or is it a bug? Can I do something to make the hardware button work?

As said above, sometimes even opening from Nautilus doesn't work and I get an error message, something like "Can not open, since the device is busy". That I consider to be even more weird - if I say "Eject!", I expect the stupid device to stop anything it's doing right now and eject the damn CD! :p
Again: Is this desired or a bug?

I'm using Kubuntu 11.10. Please ask for any other information that might be relevant.

Thanks in advance for enlightening me! ;)

Kind regards,

jhinbo

---

### Post by radioz on 2012-05-28
How old is the DVD drive? 

Optical drives are pretty cheap these days and are easy to replace. Perhaps a replacement drive would work better?

---

### Post by jhinbo on 2012-05-28
Hum, it definitely is some (>3) years old. I did not think that this might be an issue, as I haven't heard about any revolutionary breakthroughs in DVD drive technology recently. I would've thought the technology didn't change too much in that area.

But maybe I'll have to give it a try...

By the way, is the hardware button working for anyone? So I can be sure there's some problem with my PC? Or does everybody have to use the software solution?

---

### Post by pordzio on 2012-05-29
@jhinbo: does it happen on an empty drive? If not, then this looks like a drive not reporting button press to the system.
Have You tried with another flavor (e.g. xubuntu) of ubuntu booted for example from a USB drive?

---

### Post by jhinbo on 2012-05-30
Okay, Summary.

WORKS:
- While booting
- under Win XP
- while running KUbuntu 10.04 64-bit live CD (yes, I ejected the live CD)
- while running XUbuntu 10.04 live CD (yes, I ejected the live CD)
- while running Ubuntu-Netbook 10.10 live CD (yes, I ejected the live CD)


DOESN'T WORK:
- under installed KUbuntu 10.10 (software eject works)
- while running KUbuntu 9.1 live CD (even 'sudo eject' doesn't work, says 'device is busy', so this might be another issue)

It did not seem to make any difference whether the drive was empty or not.

Does this look like a bug worth reporting?

Is there any possibility to track the hardware interrupts or stuff like that, in order to see whether the button sends any signal to the system? [Sorry if this is plain nonsense, I have no idea of Kernel debugging.]

Kind regards,

jhinbo

---

