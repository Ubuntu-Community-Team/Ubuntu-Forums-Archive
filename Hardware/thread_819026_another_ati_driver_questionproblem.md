---
title: "another ati driver question/problem"
date: 2008-06-05
forum: Hardware
---

### Post by twodogsdad on 2008-06-05
Hello, I'm brand new, to Ubuntu, and I've installed ubuntu-8.04-desktop-i386, from the CD .iso, on an old Dell Inspiron 4000 that has an ATI Mobility 128 AGP 2x video adapter.

I can't get the screen resolution to be greater than 800x600. I've spent the last day or so looking at threads from others with the same or similar problems.

All solutions ultimately come down to reconfiguring the xorg.conf file. I've tried that but mine doesn't have a Subsection "Display" or any associated Modes. I tried just adding a "Display" subsection with Modes but that didn't didn't help so I just re updated the xorg.conf file with sudo dpkg-reconfigure -phigh xserver-xorg, so I think I'm back where I started... .

I've set the laptop up as a dual boot with WinXP pro and can run the monitor at 1024x768 in Windows so I know the video adapter can do it. 

Does anyone have any help they can offer?
I really appreciate it.

Thanks,
Cal

P.S. How does one copy text from the terminal window, eg the xrog.conf file, so that I can provide more detail about what I've got going on?

thanks

---

### Post by twodogsdad on 2008-06-05
My bad, please ignore this reply.

---

