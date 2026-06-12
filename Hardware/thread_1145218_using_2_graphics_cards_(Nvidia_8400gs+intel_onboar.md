---
title: "using 2 graphics cards (Nvidia 8400gs+intel onboard)"
date: 2009-05-01
forum: Hardware
---

### Post by klemperal on 2009-05-01
Here is my problem.  My Nvidia card really doesn't like doing any kind of dual display.  I can get it working, but after a reboot or two, it randomly stops working and is a huge pain to get it going again.  What I was thinking about doing, but I'm not sure if its possible,is to have my main screen plugged into the intel chip and have my second screen plugged into the Nvidia card.  If this is possible, how would I do this?

---

### Post by overdrank on 2009-05-01
Hi and what version of Ubuntu are your using? It sounds like your settings are not being saved for the nvidia graphics.  Are you using the nvidia settings ```
gksu nvidia-settings
``` to save your dual screens to xorg?

---

### Post by klemperal on 2009-05-01
Sorry for the late reply.  I'm am using ```
sudo nvidia-settings
``` to set up dual screens.  Its not that _every_ time I reboot that my second monitor stops working and goes black--its just that when it does stop working its after a reboot.  Its very odd.  When I go back and try to fix it via sudo nvidia-settings and click 'detects displays,' I can see my desktop flash on the screen, but then it goes back to being black.  Sometimes disabling the screen, re-enabling it and restarting fixes it--but not always.  Its very hit and miss and frustrating since I can't nail down exactly what the problem is or how to fix it.  Anyway, from what I've read, the 8400gs doesn't like s-video out and has given a lot of people trouble with dual screens.  I figured that If I could give my second screen the graphics card for itself and let my main screen use the onboard intel chip that things would run more smoothly.  Would this be possible?

p.s.  I'm using Ubuntu 8.10 with Nvidia 180.51 drivers.

---

