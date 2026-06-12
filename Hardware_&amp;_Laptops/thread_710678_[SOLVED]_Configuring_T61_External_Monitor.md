---
title: "[SOLVED] Configuring T61 External Monitor"
date: 2008-02-28
forum: Hardware &amp; Laptops
---

### Post by cmnorton on 2008-02-28
I have a Thinkpad T61p. I have just installed Ubuntu 7.10 on it. Now, I want to make external video work.


 My external monitor is an Acer AL194 LCD. It works fine with Windows XP, Fedora, and Ubuntu 7.10 (running on an Acer Travelmate).
 

My T61p's BIOS is configured to display to both outputs, LCD and external. The boot process is fine, but as soon as the Ubuntu logo displays, the Acer complains the input is invalid. Eventually, the Acer monitor shuts itself off, and my video is returned to the LCD display.

My LCD display is set to  1280 x 1024, but the same problem happened at lower display resolutions.
 

IBM Thinkpad Hardware Support said I needed to define a second monitor, but the display configuration would not let me hit OK -- OK did nothing and gave no error -- so I could not define the second monitor.
 

I would love some ideas on how to fix this.
 

Is this a bug, not being able to use the Screens And Graphics tool to configure the second monitor?

Edit:
-------

I de-selected the nvidia driver; rebooted; told the low resolution warning I wanted to operate in low resolution; selected a reasonable resolution 1280x; and the external monitor worked.

---

