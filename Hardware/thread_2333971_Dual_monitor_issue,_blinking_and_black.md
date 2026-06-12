---
title: "Dual monitor issue, blinking and black"
date: 2016-08-15
forum: Hardware
---

### Post by person45 on 2016-08-15
I've just upgraded to the latest LTS 16.04. I'm now having issues with my dual monitor set-up, the first monitor the cursor is blinking and the second monitor has gone black :( 

I can't get any work done!

---

### Post by irvine_himself2 on 2016-08-15
Probably a stupid question, but have you tried re-adjusting the display settings? The easiest way to get to them is through the settings manager and click on display.

If that offers no joy, the place to start is running  xrandr in the terminal. This will give basic information on what screens are connected, and, with a bit of research, will give a greater level of control than the display gui.

Finally, there are many possible reasons, including graphics driver problems. So you need to gather/provide a lot more information on the problem. If it is a driver problem, it might show up by running dmesg in the terminal. (dmesg is basically an abridged error log)

Irvine

---

