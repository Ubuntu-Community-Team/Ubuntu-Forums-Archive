---
title: "Motherboard replacement started &quot;flashing&quot; monitor"
date: 2018-11-11
forum: Hardware
---

### Post by DigiAngel on 2018-11-11
So I hope I can explain this well.  Recently I had to get a motherboard replaced....exact same type/brand.  I run xwindows and fluxbox.  My symptoms are the monitor going black for just a second, and then coming back up...almost like signal is gone like when the display has been put to sleep, but fast enough that you don't see the search for VGA or HDMI on the monitor itself.  Power is still on, and the power light stays on.  I see this behaviour:

in xwindows
in a console (no x)

but not in a bios screen.  I've tested on a different HDMI cable and monitor and I see the same results.  None of this happened before swapping out the motherboard.  I have a duplicate server that I use to hot swap and I do not see this behaviour.

So my questions are:

is there a way to "reset" my video drivers, not for X but for the system proper?
is that something I even need to do?
is there a way to monitor signal/power on the HDMI output to see if I see any fluctuations?

Thank you..this one really has me stumped.

---

### Post by slickymaster on 2018-11-11
*Thread moved to **Hardware**.*

---

### Post by him610 on 2018-11-11
I am not sure you actually have a problem. Here are the observed conditions of my monitor upon booting:
1. Power Off amber LED illuminated with black screen
2. Power ON blue LED illuminated with black screen
3. Splash screen from motherboard manufacturer
4. Grub screen
5. Black screen with blinking underscore top left corner
6. Black screen
7. Screen with background faint glow
8. Xubuntu loading screen 

How is yours different?

---

### Post by TheFu on 2018-11-11
Just guessing.

A bad/flaky power supply can cause all sorts of issues.
A failing GPU can too.  Have you tried re-seating the GPU?  Also swapping in an older GPU would be something to help eliminate the GPU as the root cause.

If the issue happens at the grub screen, it isn't X/Windows related.
If you've swapped the HDMI cable and tried a different monitor, then those aren't it.

Can you try a different output - not HDMI, but DVI or VGA?

---

### Post by DigiAngel on 2018-11-11
Thanks for the responses.  First off, this happens well after boot...device is on...i see gkrellm and some terminal sessions.  It's AFTER boot, that the blackouts will occur, and again, just a black screen for a second, and it's back...nothing else has changed on the screen.  As for the GPU, it's an onboard one and I only have one HDMI output.  This is a Dell T30 server if that helps.  Thanks again.

---

### Post by TheFu on 2018-11-12
> **DigiAngel said:**
> Thanks for the responses.  First off, this happens well after boot...device is on...i see gkrellm and some terminal sessions.  It's AFTER boot, that the blackouts will occur, and again, just a black screen for a second, and it's back...nothing else has changed on the screen.  As for the GPU, it's an onboard one and I only have one HDMI output.  This is a Dell T30 server if that helps.  Thanks again.

If it is a server, just remote into the system to do the work you need.  I have servers that I haven't physically typed on in years.  All work on them is performed through ssh from a desktop.

---

