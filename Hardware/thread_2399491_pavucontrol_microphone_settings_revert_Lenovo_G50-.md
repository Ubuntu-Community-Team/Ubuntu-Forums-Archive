---
title: "pavucontrol microphone settings revert Lenovo G50-45"
date: 2018-08-26
forum: Hardware
---

### Post by UYBGragh on 2018-08-26
Greetings!

I have read through forums and found that setting pavucontrol front left and front right to different levels makes the microphone work. In my case, it **does** work, but only until I try to use it. At that point I get between three seconds and a minute of working time, then the sliders reset themselves to the same value leaving me with a non-working microphone. Again, the device works; this is not a hardware issue. It is a matter of a particular configuration not holding in pavucontrol it seems.

This is with both the built-in and an external mic on a Lenovo G50-45 running Lubuntu 18.04.
The external mic is a headset that connects via a single 1/8" connector.
I am watching the gauge in Pulse Audio Volume Control as well as the wave form on an online mic test site.

Thank you.

---

### Post by UYBGragh on 2018-08-26
Oh, and this is on Lubuntu 18.04.

---

### Post by UYBGragh on 2018-08-27
OK, I think I have this licked. TLDR: Using Google Chrome on Ubuntu 18.04 to use a microphone will trigger the phenomenon described.

Using Google Chrome for anything involving the microphone such as facebook chat will cause the left and right channels on the Input Devices tab to realign with each other, making them cancel out and effectively disabling the microphone.

Confirmed with Ubuntu 18.04 with Chrome and FF, LXLE with Chrome never installed, and  Lubuntu 18.04 with Chrome.  Also, I used multiple mic test sites. I'm monitoring the Pulse Audio Volume Control as I write this, and it is responding to key presses, my air conditioner, and my occasional cough.

I don't know for sure if this is an issue with Ubuntu or Chrome, but it does appear the combination of them triggers the event. I'd be curious to know whether this behavior can be triggered on different laptops and different hardware configurations.

Marking as SOLVED and hoping this helps someone else.

---

