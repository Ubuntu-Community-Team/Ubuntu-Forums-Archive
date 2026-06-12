---
title: "DVI-D output not working with Nvidia GeForce 7900 GS and proprietary driver v. 185"
date: 2010-01-01
forum: Hardware
---

### Post by pansapiens on 2010-01-01
I just spent a few hours diagnosing this issue, so I thought I'd document it here for the search engines. The short version: my DVI-D output does not appear to work with the proprietary Nvidia accelerated graphics driver version 185, but it does work with version 173.

The long version:

I have an Nvidia GeForce 7900 GS card that has two video ports: a DVI and a VGA output. Under Jaunty (9.04) this card worked with the DVI-D output, but *only* in 'graphics mode' (eg, Xorg graphics. Framebuffer graphics, BIOS bootup text and the text mode console were only visible using the VGA port, *not* the DVI port). I'm using a Phillips 220WS LCD monitor, which can be fussy about resolutions etc, but I don't think this is root of the problem.

After upgrading to Karmic (9.10), the DVI-D output stopped working altogether. The VGA ouput still worked fine for both 'graphics' and 'text' modes. Various reboots with video cables attached or unattached, and the LCD monitor on or off didn't help - the DVI-D output still wasn't working.

The [Recommended] proprietary Nvidia driver for this card under Karmic is version 185. The simple solution - downgrade to use driver version 173.

eg. *System -> Administration -> Hardware Drivers* .. select Nvidia accelerated graphics driver (**version 173**) .. press Activate. Reboot.

The DVI-D output now works as before - I get graphics as expected under Xorg, but still nothing under text-mode (or framebuffer mode). Good enough for my purposes.

---

