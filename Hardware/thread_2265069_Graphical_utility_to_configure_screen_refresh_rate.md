---
title: "Graphical utility to configure screen refresh rate"
date: 2015-02-12
forum: Hardware
---

### Post by Molech on 2015-02-12
Hi.
I'm using Ubuntu 14.04x64 to make and (trying) to present lessons in my classroom.
The thing is, when I connect the classroom projector on my VGA port the projector says "Refresh rate out of range" and it exhibits no image at all.
Looking for answers I found about xrandr and how to set the resolution and refresh rate via terminal window.
Then I looked again for a GUI and found Arandr, but it seems to provide only resolution config, not refresh rate. That is already possible via system settings, which made this utility useless.
Is there any utility that can handle the screen/projector refresh rate?
I think that should be on the default screen/monitor options under system settings.
Thanks.

---

### Post by TheFu on 2015-02-12
lxrandr, xrandr, arandr are the tools ... or you can modify /etc/X11/xorg.conf manually and restart X11.
lxrandr has frequency on the GUI.
Of course, you could create a trivial script that sets what you want for the projector with xrandr. That would be faster than screwing with any GUI tool, IMHO.

---

