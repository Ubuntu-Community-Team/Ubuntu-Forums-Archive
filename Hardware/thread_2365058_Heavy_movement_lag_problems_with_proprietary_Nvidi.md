---
title: "Heavy movement lag problems with proprietary Nvidia drivers"
date: 2017-07-01
forum: Hardware
---

### Post by Megadoomer on 2017-07-01
Hello everyone,

I believe this may be a known issue, but I am unable to find a solution.

I recently bought a new graphics card (Nvidia Quadro K5000) for 3D modelling and video editing. After installing it to see if everything works, as soon as I started my system, I noticed heavy stuttering all around. I thought that it was an issue with the Nouveau driver, so I installed the proprietary (tested) Nvidia driver from the settings menu. Unfortunately, this did not solve the problem. In fact, whenever there is any kind of animation/movement happening (moving windows, scrolling or open/close animations), the whole system is lagging, it seems. However, videos can be played without any problems or stutter.

Installing the legacy driver did not solve the issue, is there anything I can try to solve this?


Kind regards!

---

### Post by Autodave on 2017-07-01
Which driver version did you actually install?  If you go into Settings -> Additional Drivers, that should pick the one that you need. Let it install and reboot. Then, you can go into the Nvidia settings and tweak the card between performance and quality.

---

### Post by Autodave on 2017-07-01
I just checked Nvidia's website and it is calling for the 375.66 driver. That driver is in the repositories.

---

### Post by Megadoomer on 2017-07-02
> **Autodave said:**
> Which driver version did you actually install?  If you go into Settings -> Additional Drivers, that should pick the one that you need. Let it install and reboot. Then, you can go into the Nvidia settings and tweak the card between performance and quality. I just checked Nvidia's website and it is calling for the 375.66 driver. That driver is in the repositories.

That's the driver version that I have currently installed. Although I also tried the legacy driver and that made no difference to the issue.

I've played around with the Nvidia settings and tried some reported fixes and somehow, my current setup seems to fix all tearing and lag issues. Unfortunately, I don't know the exact setting responsible for solving the issue.

However, I first disabled the "Sync to VBlank" and "Allow Flipping" options in the driver OpenGL-settings, which made the window movement lag go away, but resulted in tearing. I then added both: ```
Option &#8220;TripleBuffer&#8221; &#8220;True&#8221; 
``` and ```
Option "metamodes" "... { ForceFullCompositionPipeline = On }"
``` in the /etc/X11/xorg.conf file and after that didn't completely solve the tearing issues, I reenabled "Sync to VBlank" and "Allow Flipping" in the driver settings, so that is the current setup.

I still have one problem though: Every time I reboot, I will have lag of the mouse pointer, window dragging, animations and tearing until I open the Nvidia X Server Settings from the application launcher. Immediately after openening the settings window, all symptoms vanish and I have no issues anymore. I thought that this was a startup problem, so I tried adding ```
nvidia-settings --load-config-only
``` first to the startup applications and then into /etc/X11/xinit/xinitrc, but neither worked. I still have to launch the Nvidia settings window manually every time I reboot to remove any lag and tearing.

Does someone have any idea on how to solve this?

---

