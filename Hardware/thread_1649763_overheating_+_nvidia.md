---
title: "overheating + nvidia"
date: 2010-12-20
forum: Hardware
---

### Post by RussellEngland on 2010-12-20
I've got a Samsung NP-R700-AS07 which has a NVIDIA GeForce 8600M GT

Since I upgraded from 10.04 to 10.10 my laptop keeps overheating. 

I've installed xsensors 0.70 which reports the temp about 82 degrees C.

I stopped processes I didn't need in the start up  - but this didn't change the temp.

I then tried installing the nvidia drivers using the instructions at:
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

This reduced the temperature successfully down to 58 degrees C. But the screen is very dim and difficult to see. I tried increasing the brightness via the nvidia x-server settings but its still too dim - can't explain it any other way really. 

So I deactivated the nvidia driver but when I booted up it took me to the prompt saying there were no screens. So I booted up in recovery mode and chose the default generic display, but now the temperature is back up to 82 degrees C, grrr...

Any ideas what I can do to resolve this? The nvidia display is just too dim - is there a generic display that doesn't over heat my laptop?

Many thanks.

---

### Post by PhantmKllr on 2010-12-20
Check the Nvidia website for an officially supported driver.

---

### Post by RussellEngland on 2010-12-22
Thank you for the reply, I installed the drivers from

[http://www.nvidia.co.uk/object/linux-display-ia32-260.19.29-driver-uk.html](http://www.nvidia.co.uk/object/linux-display-ia32-260.19.29-driver-uk.html)

but the screen is still too dim. 

The only way I can describe it - its as if the power saving is on and its dimmed the screen. Yes, I have checked the power management.

Is there a way to improve this? Or is there an alternative display I can use without increasing the temperature?

This has never been a problem until I upgraded to 10.10 - I'm either stuck with a dim screen, or deactivate nvidia and wait for my laptop to switch off because its too hot. :(

---

### Post by PhantmKllr on 2010-12-22
Have you ever opened up your laptop and cleaned out the ventilation system?

---

### Post by Fir3chi3f on 2010-12-23
I was actually going to suggest the same asPhantmKllr, I don't know how hard it is on this laptop but it's amazing how clogged the fans/heat sinks get on laptops. 

Are there any settings for the dim/brightness in the bios? is there an fn combo key that you can use to raise the brightness?

---

### Post by T.J. on 2010-12-23
Hello RussellEngland,

I think it's possible you might have a fan issue, but I'd like to offer a suggestion or two  - in the hope they will be useful.  I hope I don't sound condescending.  I'm just going to throw them out there, and please let me know if you need more information.


1) Change the driver.  The Ubuntu archives usually contain at least two versions of the proprietary driver,  Do both yield the same result?  You might need to reinstall Mesa (OpenGL libraries) if you manually installed your own driver, then removed it.  The NVIDIA installer from NVIDIA can make a mess of those.

Can you please tell me the driver version you are using?


2)  Are all the settings in the NVIDIA settings program at default position?

3) Has the brightness been failing for a while, before you upgraded?  If so you might need to have the backlight replaced if it had a "last gasp".

---

### Post by RussellEngland on 2011-01-03
Thank goodness for that... Finally found an answer purely by accident.

The nvidia driver is broken according to [https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia) so I was following the instructions.

I typed nvidia into Synaptic Package Manager to pick the proposed driver and spotted "smartdimmer ... change LCD brightness on Geforce cards"

So I ran smartdimmer in a terminal, increased the brightness and all looks great now!


I will still need to open the laptop and clean the fan at some stage but at least I can see the screen now.

Thanks for all the advice, Russ

---

