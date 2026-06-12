---
title: "touch screen monitor detection"
date: 2014-03-08
forum: Hardware
---

### Post by Tom_R2E3 on 2014-03-08
Hi.  I've done a fair amount of searching but haven't managed a solution to my problem.  I am new to Linux, which is making things more tricky.

system: Intel D525MW
OS: Ubuntu 10.04 (with LinuxCNC real time kernel)

I'm trying to use a touchscreen monitor via USB.  Ubuntu detects it (as eGalax touchscreen) and registers a touch correctly.  However, every touch moves the curser to the top left corner of the screen, regardless of where you touch.

I have used Xinput_calibrator to arrive at calibration numbers (using the mouse to click the targets), but this has no affect on the curser location via touch input)
Using Xinput set-prop I can invert the screen such that every input registers in a different corner, but never anywhere but one of the corners of the screen.

I notice that Ubuntu detects my display resolution correctly, but shows the screen size as 33" when it is actually 17".  Could this be something to do with why all my touch inputs are seemingly off the screen?

Any help appreciated, I'll do my best to provide the necessary information.

Thanks in advance

tom

---

### Post by sammiev on 2014-03-08
Welcome to the forums. Ubuntu 10.04 is no longer supported or updated. I'm not really sure if you will be able to get it going. Ubuntu 12.04 is the current LTS version and good for years to come.

---

### Post by Tom_R2E3 on 2014-03-08
Hi sammiev, thanks for your reply.

I'm stuck with 10.04 because I'm using the computer for LinuxCNC (to control a milling machine).  So I cant only update if the developers compile it with a newer LTS version.  

I thought there might be a way to set the screen size manually? rather than relying on auto detection? Although I'm not sure this is what causes the touch screen problem.

---

