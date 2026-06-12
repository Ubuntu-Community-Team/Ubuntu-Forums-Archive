---
title: "Blank hdmi external display outside of X"
date: 2009-12-17
forum: Hardware
---

### Post by merindol on 2009-12-17
Hi there.

It's more a hardware problem than an Ubuntu problem, I think, but maybe there is a workaround.

I'm using a HP DV7-1145ef laptop with a **HDMI output**. I'm also **using an external display** (HP 2275W) with a DVI input. Both are linked with a HDMI/DVI cable.

**I configured X and the dual screen works fine. But, it's working only under X.**

**If I switch to a console tty the external screen goes to sleep mode** (not the same as if I unplug it). It seems it gets no signal from the laptop.

Also, the external screen stays blank during the booting process. It only gets a signal when GDM is fired up.

Maybe that's normal (it's my first external screen plugged on a laptop). Maybe it's due the HDMI interface.

Is there a way to configure something so I can see the boot process (because most of the time I let the laptop closed with papers on it :p).

Best regards.

---

### Post by phelge on 2011-03-30
Hi

I know it's an old thread, but I have still the same problem with Maverick. I've an HP 8710W laptop to which is connected a Dell Monitor U2410 via an HDMI (laptop) to DVI (Dell Monitor) cable. Here are my issues :

Power on the HP laptop, I can see the HP splash on the Dell

1st issue : The grub boot menu is displayed on the laptop screen while the Dell goes to sleep mode. Boot sequence is displayed as well on HP laptop screen.

The Dell monitor wake up when entering gnome startup (Before I've configured the Dell monitor in nvidia-settings). Note that I have no issue with X/gnome on the Dell.

2nd issue: If I press Ctrl-Alt-Fn to go to a console, this is one more time displayed on HP laptop screen and nothing on the Dell.

3rd issue: Leaving the gnome session by a restart makes everything goes black. The laptop is still on but nothing on the screens. Typing blindly some commands do nothing. Only solution is to reset the laptop with power button.

I don't know if these are different causes giving these issues, but I would really appreciate here to have some hint from those who have solved one of them.

Thanks

---

### Post by phelge on 2011-04-07
bump

---

