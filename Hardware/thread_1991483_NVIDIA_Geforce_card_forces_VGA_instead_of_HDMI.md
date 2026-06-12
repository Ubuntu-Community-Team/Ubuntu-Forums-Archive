---
title: "NVIDIA Geforce card forces VGA instead of HDMI"
date: 2012-05-30
forum: Hardware
---

### Post by Tijn1978 on 2012-05-30
Hi Everyone,

My problem is as follows.
I am trying to make Ubuntu use my HDMI cable instead of my VGA cable. I have searched forums and websites over and over.
I have the proprietary drivers installed. I have all nvidia "tools".
I have reconfigured the xserver with dpkg. I just can't get ubuntu to use my HDMI cable. The cable is plugged in in both my pc and monitor. I am not sure what info to post.
Some info isn't in NVIDIA xserver settings dialog (see attachment).
A link to another thread would suffice. I'd be more than happy to write a short howto at the end of this thread the moment it works.

Kind regards,
Tijn1978
:confused:

:edit: 
This needs to be moved to another site of this forum (sorry :( )

---

### Post by papibe on 2012-05-30
Hi Tijn1978.

A few questions:

Are you connecting 2 different monitors using 2 different cables?

Is the HDMI cable a pure HDMI cable? (not VGA->HDMI or DVI->HDMI)

Regards.

---

### Post by Tijn1978 on 2012-05-31
> **papibe said:**
> Hi Tijn1978.

A few questions:

Are you connecting 2 different monitors using 2 different cables?

Is the HDMI cable a pure HDMI cable? (not VGA->HDMI or DVI->HDMI)

Regards.

No, both a VGA and a HDMI cable are connected to my monitor.
Two cables from pc to monitor.

Greet,
Tijn1978

---

### Post by papibe on 2012-05-31
Thanks.

Monitors that allow several inputs (I have one of them), only receive one signal at a time. The input it is usually selected through a hardware switch (usually a front button).

Although this behaviour is similar to a HDTV, I don't think it guarantees that non selected inputs are going to respond to external signals.

I would suggest to use just one connection to the monitor.

Turn off your computer, disconnect the VGA cable, keep the HDMI, and turn your computer back on.

I hope that helps, and tell us how it goes.
Regards.

---

### Post by Tijn1978 on 2012-05-31
You are my hero papibe,

I cannot believe it was that easy. I unplugged everything but the hdmi cable. Rebooted my ubuntu-box and voila!
I also found out that I was installing the NVIDIA driver over the old one which btw was the exact same version.

Thank you so much!

Tijn1978
:P

---

