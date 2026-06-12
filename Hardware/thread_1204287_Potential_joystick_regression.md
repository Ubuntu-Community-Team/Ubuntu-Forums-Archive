---
title: "Potential joystick regression?"
date: 2009-07-04
forum: Hardware
---

### Post by Surlent777 on 2009-07-04
I have a Logitech Dual Action USB game pad, and it worked right out of the, er, plastic with Intrepid. No issues at all, and I installed the standard apt-get joystick stuff, ran jscalibrator, and everything was good. Now, on this same system, I upgraded to Jaunty and discovered strange problems. Now, jscalibrator and it's command-line equivalent all pick up everything just fine on their test screens and while calibrating.

However, most apps I've tried with it refuse to acknowledge the digital pad, the exceptions being the calibration utilities and, oddly enough, ZSNES, although ZSNES' detection isn't perfect, as it doesn't always properly pick up on an axis change. For instance, if I'm holding right, and then press up or down, usually it keeps acting as though right were being pressed still. I have to actually release right and then press down to make it work.

Now, with things such as Gens/GS and FCEU, I can press the joystick's MODE button and swap the left analog stick with the d-pad, which tricks the d-pad into working with those two apps, but this obviously isn't ideal, and ZSNES still doesn't play nice with this. 

Also, even though it's calibrated,  jscal -t /dev/input/js0 tells me "jscal: axes not calibrated". This is all true even on a freshly installed system (I did a reinstall for the sake of optimization, also going from 32 to 64-bit). Anyone have any ideas on what I might do?

---

### Post by Surlent777 on 2009-07-05
I feel I should also mention that an XBox 360 controller I plugged in seemed to work quite well and was picked up and usable immediately,, even in ZSNES, though I couldn't test the d-pad due to it being broken anyway.

---

### Post by RobbMeex on 2010-01-03
I might suggest deleting /home/yourusername/.joystick
My SNES pad wouldn't work properly after running jscalibrator. then I deleted that file and reset.

---

