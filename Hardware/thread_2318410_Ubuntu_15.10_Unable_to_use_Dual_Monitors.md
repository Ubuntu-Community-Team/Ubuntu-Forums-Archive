---
title: "Ubuntu 15.10 Unable to use Dual Monitors"
date: 2016-03-25
forum: Hardware
---

### Post by bakpakin on 2016-03-25
I'm running Ubuntu Gnome 15.10 on a Lenovo Thinkpad p50. Everything is working quite well right now, (for the most part), as long as I am only using my main laptop monitor. When I plugin my external monitor, however, the desktop immediately crashes and seems to flash every second or so as it repeatedly crashes. On screen, I get a great view of the system logs or something( I'm quite new to ubuntu and linux in general, coming from a mac background). I can still get into terminal with f4, though, and everything seems fine on the command line.
 
While the problem could be a number of things, I believe it to be something wring with the display driver. I'm running the Nouveau display driver on an Nvidia QuadroM1000M. I would rather not switch to the Nvidia Drivers, as they have other strange issues like horrible screen tearing which I cannot fix, as well detecting my two displays as one large display.

---

### Post by Bucky Ball on 2016-03-25
Welcome. Just a suggestion: have you tried switching the machine completely off, plugging in the monitor then powering up? Same issue? Describe what happens, please.

Jabbing the monitor in while the system is up may be causing some strange issues. Never know. It may be that the monitor is grabbing some odd resolution when pushed in while the machine is running. Having it there from boot might give it time to recognise, have a think and grab the right res. :-k

---

### Post by bakpakin on 2016-03-25
Thanks for the reply.

Yes, I have tried booting from having the external monitor plugged in. The result is no different. I'll try again in a little bit, but I'm pretty sure that It just fails at login or immediately after login. Maybe I've forgotten to do this, though.

---

### Post by bakpakin on 2016-03-25
Ok, Having tried that, My monitor is now just completely not detected. Now, regardless of if I turn my computer on with the HDMI cable connected or not, the display is not even detected. Taking the cable out and putting it back has no effect.

---

### Post by Bucky Ball on 2016-03-25
You say 'the desktop crashes'. Do you mean the desktop environment on the monitor crashes and goes to terminal drivel or the whole system crashes so you have nothing on the laptop screen either?

If you can still see the laptop screen fine, have you tried looking in 'Display' and seeing what the machine thinks you have plugged in?

---

### Post by bakpakin on 2016-03-27
The whole desktop environment crashes. I have to unplug the monitor, use alt f4 to grab a terminal, and then either restart the computer, or I could probably restart gdm.

---

