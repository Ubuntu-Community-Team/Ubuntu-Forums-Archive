---
title: "monitor stopped working with Nvidia 8600GT"
date: 2008-02-26
forum: Hardware &amp; Laptops
---

### Post by Dave2009 on 2008-02-26
I have my new computer setup to dual boot with Windows XP Professional and Ubuntu 7.10 and everything has been working fine until today when I tried to setup Ubuntu to run my television as a second monitor.

Now whenever I try to boot into Ubuntu I get nothing but a black screen and my monitor keeps turning itself off because it is no longer getting any output from the graphics card.

[COLOR="DarkOrange"]I went through the instructions for setting up twinview and the instructions required prior to this step to setup and back up the xconf file. Unfortunately I cant supply links for the tutorial because they where only available to me on Ubuntu (which as you know I can no longer see)

Once I had done the above I still had no dual monitors and my desktop had partially extended itself off the screen and was displaying at 1920x1280 instead of the previously correct default of 1680x1050.

Naturally I wanted to fix this new problem as well as the Dual Monitor one so I looked for more info.

After I followed the above tutorials I found that they where a bit old and that there is now an Nvidia control panel that is available with sudo apt-get. I installed this and set up a TV as a second monitor.

These are the settings I put into Nvidia's control panel, 1680x1050 for my primary monitor and 800x600 for my TV with the TV on the left hand side of my primary monitor. I then saved these settings and also saved them to xconf using the xconf button.

This is where my problem of not getting any output at all from my graphics card for my monitor began, and now whenever I try to boot into Ubuntu I see nothing but pitch black and my monitor switches itself off. 

I know ubuntu is still working because I can hear the ubuntu start up theme after I have successfully logged in (which I can still do despite not seeing the login screens)

Windows XP which is running off a different partition on the same drive is still working fine with both monitors, this is strictly an problem with ubuntu and nothing to do with any of my hardware.
[/COLOR]
Does anyone know of how I can fix this? 

I was thinking of just reinstalling Ubuntu and starting over from scratch but I am afraid that I wont be able to do this without destroying my other partitions, I dont want to destroy my XP install which is on the same disc.

---

### Post by Dave2009 on 2008-02-26
Fixed it by restarting in recovery mode.

I think I will just have to wait a year or two for a version that correctly supports dual monitors out of the box.

---

