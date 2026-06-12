---
title: "Dual Monitor Trouble"
date: 2010-05-11
forum: Hardware
---

### Post by kingofheights on 2010-05-11
I recently finishing building my desktop system.  It uses an GeForce 9800 GT with a monitor hooked up to each output on the graphics card.

So after installing Ubuntu, the OS didn't know how to handle two monitors.  It displayed the same thing on both monitors.  So I took some of the OS's suggestions, and installed some nVidia restricted drivers ("NVIDIA accelerated graphics driver (version current)[Recommended]").
 

 But then I had a different problem.  The OS knew how to use both monitors, but it looked like it used a separate desktop environment for each monitor.  (The right monitor doesn't have all the launcher icons that the left has.  Also, windows don't transfer from one monitor to the other.)  I tried switching the nVidea driver that I was using ( to “NVIDIA accelerated graphics driver (version 173)”), but the same problems continued.
 

 I have also tried going to “System > Preferences > Monitors”.  When I try this, I get a dialogue box that says “It appears that your graphics driver does not support the necessary extensions to use this tool.  Do you want to use your graphics driver vendor's tool instead?”  The problem with the graphic driver vendor's tool is that I don't know how to use it.  Can someone help me with this?

---

### Post by rethgir on 2010-05-11
Sounds like you're using separate X screens instead of TwinView. To enable TwinView go to "System > Administration > NVIDIA X Server Settings". 

The setting dialog will open. You want to select "X Server Display Configuration" from the left panel. 

On the right hand side you should see something like "Configuration: Separate X screen" with a "Configure..." button. Press the "Configure..." button and select "TwinView". You will have to restart X... hope this helps!

---

