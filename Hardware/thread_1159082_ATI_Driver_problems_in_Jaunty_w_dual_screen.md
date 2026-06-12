---
title: "ATI Driver problems in Jaunty w dual screen"
date: 2009-05-14
forum: Hardware
---

### Post by esplosion on 2009-05-14
Okay, long story short(er).  Added 9.04 to my work machine in order to facilitate moving from Windows to Ubuntu, mostly for fun, really.  Install worked fine, no problems.  I boot into Ubuntu and check the Hardware Drivers section, where it lists a proprietary driver for the ATI Radeon 2400 HD Pro that my machine has.  I want this installed because the default driver doesn't support basically anything complext at all, even as far down as the visual effects, much less 3d.

So I install and start running into problems.  Basically, any time I have this driver loaded and I try to run, well, anything, the second monitor (video card is dual vga out) blinks in various areas and the system slows to a crawl.  After a very long time, if ever, the app comes up and the second monitor may or may not continue to blink.  

I figured, okay, the fglrx driver that it installed is tripping out, I will try something else.  I deactivate the driver from Hardware Drivers, and I install Envy.  Envy comes up with 1 suggestion for a driver and I install that.  Same deal.  

Now, I am not a novice with Linux, but I am not really far from it.  I am a Systems Engineer, so I understand the ideas of what is happening well, but not the exact way to do it in this environment.  

So, I tell Envy to drop the driver and I go back to default.  Someone pointed me to [http://packages.ubuntu.com/hardy/x11/xserver-xorg-video-radeonhd](http://packages.ubuntu.com/hardy/x11/xserver-xorg-video-radeonhd)
and I downloaded the package, but am unsure how to know if I am using the driver or not, though 3d and visual effects still aren't working.

Suggestions?

---

### Post by peedeeramone on 2009-05-25
if you open catalyst control center and it doesnt tell you catalyst isnt installed then it probably is. 

i dont know of a better way. i know theres a command to diplay it, but i dont know what it is. maybe someone else can help you.

good luck. i cant get dual screens to work either. i have a radeon card also and when i try to use the display setting i get super slow speeds untill a minute or so after i can get the display gui to close. im digging to find an answer myself

---

### Post by charonred on 2009-08-18
I'm having the similar dual monitor probs as mentioned above with a Jaunty install (my Hardy install works fine); had some help getting 2nd monitor to display to display in Jaunty, but not perfect.

you may want to checkout replies and suggestions from my thread
[http://ubuntuforums.org/showthread.php?t=1227751]("http://ubuntuforums.org/showthread.php?t=1227751")

I was going to try going back to my EAH2600 Pro card (dual DVI outputs), but by the sounds of this thread, that probably won't fix the issue either

So it seems that with or without restricted drivers, Jaunty just doesn't want to run dual monitors on ATI cards - so for the moment I think I'll stick with Hardy.

Jaunty seems ok with single monitors as I've done several installs and things work fine; but dual monitors are a problem.

See if dual monitors at least run under Hardy Live CD; if so, then an install of that should work and it should then work with restricted drivers once installed.

---

### Post by markbuntu on 2009-08-18
The latest drivers from ati (9.7,9.8) work a lot better with multiple monitors on Jaunty. There was a problem with randr1.2 that has been resolved.

I have not tried the 9,8 driver yet but 9.7 was very easy to set up dual monitors with the Catalyst Control Center, compiz and everything. It was also fairly easy to set up 3 monitors on 2 gpus but no desktop effects were available with that setup.

This was not true with the 9.3-9.6 drivers where you had to manually disable randr and use xinerama in Jaunty.

I have never had a problem setting up dual monitors on a single gpu in Hardy using the drivers from ati. ( I still use Hardy as my main OS)

---

