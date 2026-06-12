---
title: "htop running at 20%"
date: 2009-06-05
forum: Hardware
---

### Post by acoccimi on 2009-06-05
Hello,

I have recently installed Eeebuntu 3.0 on my EeePC 701. I have the CPU scaling applet in the panel. Whenever it is set to OnDemand, I open up htop and it shows itself running at 20%, with X being the next highest process (also around 20%). However, when I set the CPU scaling applet to a fixed clock speed, it only runs at around 5%. I don't mind having my CPU set to a fixed rate, but I want it to either start up like that (it automatically goes to OnDemand on boot, and I read about how the functionality of setting the default was removed (not that I agree)) or fix my CPU usage problems, because even 5% is a little high for htop.

Also, every so often nautilus sucks up the CPU's power - I think it is some autofs thing, but I don't know what that is, whether I should disable it, how to disable it, and how to keep it disabled on boot.

And finally, the fan is turning on and off very intermittently, and it's becoming annoying. I believe this is because the CPU temperature fluctuates between 58-60 a lot (Vancouver's experiencing a heat wave - sorta). I changed the TEMP_WARN value in eeepc-acpi.local to 65 instead of 60, which should mean that it will turn the fan on after it hits 65, but it is still coming on at 60. And I made sure that "FAN_MODE" is set to managed/MANAGED.

Besides these, I don't know anything else I would want to change on this great system - dual head monitors are working, 3d acceleration works (it works better on the default setting rather than setting AccelMethod=UXA in xorg.conf), and bluetooth is working out of the box (unlike Intrepid).

Any help to these problems would be appreciated. Thanks in advance! :D

---

