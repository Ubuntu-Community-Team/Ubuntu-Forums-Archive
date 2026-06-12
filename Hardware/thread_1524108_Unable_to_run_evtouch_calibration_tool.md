---
title: "Unable to run evtouch calibration tool"
date: 2010-07-04
forum: Hardware
---

### Post by nufan.us on 2010-07-04
Hi everyone.

I'm having some problems calibrating my touchscreen
I've tried to figure out a solution for this problem for approximately three days now, and I'm completely stuck.

I've searched this forum and google high and wide, and no solution so far.

My machine is a Fujitsu-Siemens Lifebook B2154, on which I recently installed Ubuntu 10.4. My problem is that the touchscreen is recognized and functioning, but is highly miscalibrated. When I try to follow the instructions for the evtouch driver, and return to a terminal, kill X and try to run the calibrate.sh, it gives me a "zenity"-error, saying "cannot open display: "" ".
The error is repeated no matter if I try to run the script via "sudo" or "su".

I then tried to run the "ev_calibrate" directly in X instead, but it gives me the error "XLoadQueryFont: failed loading font '*freemono*'"

Does anyone have any idea how to fix this problem, and get the calibration tool working?

I tried the calibration tool for the old lbtouch driver and that almost works, except that it gives me some completely outrageous values, but it starts up perfectly fine.

Anyway.. I hope someone can help me out there..
Thank you in advance for your time and help..

---

