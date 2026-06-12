---
title: "Ubuntu 14.04.3 LTS Mouse getting stuck in to right of screen"
date: 2015-11-23
forum: Hardware
---

### Post by ashe2 on 2015-11-23
So i'm new to Ubuntu i downloaded Ubuntu Desktop 14.04.3 yesterday, and from the beginning going through the installer in the "try Ubuntu without installing" in the fulling downloaded version all of it and every time my mouse gets stuck in the top right corner of the screen i can move it slightly but when i do it just starts flying all over the screen and randomly clicking on things. This makes using Ubuntu impossible as i can only use my keyboard and that doesn't get me to far. i have tried everything i can think of i have tried different mice even an old roller mouse i had lying around nothing works i have even reinstalled  Ubuntu completely if anyone knows what the proble is or how to fix it that would be EXTREMLY helpful. Thank you.

(P.S: i am using a Razer Naga Hex mouse)

(Fixed it just used "sudo xinput set-prop 15 147 0" (i think it was just thinking that i had a touchpad but i was actually using a mouse so i had to turn off the touchpad not 100% thats actually what it was but this fixed it so im happy)

---

### Post by mörgæs on 2015-11-23
Hi, welcome to the fora.

Let's see the hardware. Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

