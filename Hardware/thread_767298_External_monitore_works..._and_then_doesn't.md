---
title: "External monitore works... and then doesn't"
date: 2008-04-25
forum: Hardware
---

### Post by Floep on 2008-04-25
Hi everyone,

I'm totally new to Linux/Ubuntu,so I hope you can help me out. I did some research on my problem but nothing seems to help. So here goes.

Basically my problem is that my external monitor (Samsung 2232bw) doesn't work with my laptop (old Compaq presario 2165EA). However! It DOES work when the computer is starting up. I get the Ubuntu logo on both my screens, but when the login screen appears, the external monitor loses signal. So it doesn't just go black, it actually loses signal. Before that I see it struggling between analog and digital input (the on screen display switches between "analog","digital", "analog" etc. It's analog).

So thats it! I hope you can help me out, cause I really want to use Ubuntu... thanks in advance!

---

### Post by gadget_hacker on 2008-04-25
You will probably need to provide more information so someone can help you quicker and more efficiently.  Do you know what kind of video card you have?

---

### Post by Floep on 2008-04-25
Oh right: the video card is a ATI Mobility Radeon...

---

### Post by gadget_hacker on 2008-04-25
Do you know if you have selected to use the restricted drivers for ATI?  look at system->administration->hardware drivers.

---

### Post by mephisto56 on 2008-04-26
Same problem here (post: [http://ubuntuforums.org/showthread.php?t=765169](http://ubuntuforums.org/showthread.php?t=765169)). I'll be following this one since right now working on ubuntu is just a pain in the *** because of these problems.

---

### Post by markcgriffiths on 2008-04-26
I have pretty much the same setup except I have a Presario 2500 and a Philips 22".  I have tried with and without those ATI drivers, they do not help.  I have the x300 Radeon mobility card.

---

### Post by Floep on 2008-04-26
So you both have the same problem? It also works at first, showing the Ubuntu logo, and then stops working?

Well, in that case, at least I'm not the only one...

---

### Post by markcgriffiths on 2008-04-27
Please, can anyone help?

---

### Post by TeleTommy on 2008-04-27
What happens if you start up without external TFT and connect later on?

---

### Post by markcgriffiths on 2008-04-27
Nothing, it's still black.  I only see something before the login window regardless.

---

### Post by TeleTommy on 2008-04-27
same issue with me

[http://ubuntuforums.org/showthread.php?t=770616]("http://ubuntuforums.org/showthread.php?t=770616")

---

### Post by markcgriffiths on 2008-04-28
I have created a bug about this as no one appears to know the answer:

[Bug Report]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/223593")

---

### Post by codamNO on 2008-04-28
Are you sure you dont have a hotkey to switch between monitor configurations?

I experienced exactly the same symptoms as you described on a HP dv6060 laptop. I'm pretty sure that what's happening is that the BIOS is defaulting to a cloned display, then when OS takes over control it is defaulting to a single display.

My hotkey functions as it should once in Ubuntu, but I cant get any further than a cloned display with the external being stretched to the same resolution as the laptop display. In the screen resolution applet I get no response when I click "detect displays", even though I have a cloned display up.

To the OP. The message you are getting regarding switching from anologue to digital is just the syncmaster's way of saying "no signal".

---

### Post by syarost on 2008-04-28
I am having exactly the same problem with my Dell Inspiron 1705 laptop (NVIDIA 7900 GS, Core 2 Duo 7400).  The external monitor worked (via Fn-F8, after boot-up)) through the last beta.  When it upgraded to the released version of 8.04, the external monitor stopped working.  It uses the external monitor while booting, then defaults to the built in monitor.  The Fn-F8 no longer works.

---

### Post by markcgriffiths on 2008-04-28
"Are you sure you dont have a hotkey to switch between monitor configurations?"

I tried that, it has no effect.

---

### Post by mephisto56 on 2008-04-28
Don't know exactly the steps but in xubuntu I have something workable now with sudo displayconfig-gtk. I first messed it up (actually ubuntu did as it couldn't remember what my laptops monitor was and what my 2nd upon reboot). I got a low resolution screen upon login and only set my second monitor there as my primary one (disabled the other) and now it uses the plugged in one if it's plugged in on reboot and and my laptops one if my second one isn't connected.

Don't know if that makes sense but it seems to work. So first step is to do everything right and let (x)ubuntu mess up. That's the easy part.

---

### Post by markcgriffiths on 2008-04-28
Hi and thanks,

It was a good idea but if I do that then the "monitor and settings" app crashes.  The external monitor comes off standby but is always black and then the original settings come back.

---

### Post by syarost on 2008-05-03
I have tried using the command "sudo displayconfig-gtk" to bring up the display tool.  I can get video sent to the external monitor, but have been unable to get the resolution correct. Perhaps this will solve your problem.

When I messed up my video beyond repair, I used "sudo dpkg-reconfigure xserver-xorg" to regain the video on my laptop screen.

---

### Post by Victor516 on 2008-05-05
I have the same problem with my laptop using external monitor because the built in one is broken. I used the BackTrack 2 live cd and the display works on there, So is there anyone that can guide me through using the drivers or configuration that are in use on that. I am new to linux.

---

### Post by beyboo on 2008-05-31
I face somewhat the same problem on my Acer 5920 with Hardy. Has an intel X3100 adapter. I have added my comment to the bug with a work around I currently use. 

[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/223593](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/223593)

---

### Post by syarost on 2008-06-03
A work around to allow use of an external monitor if you have an NVIDIA video card is to load EnvyNG, then use the NVIDIA Settings tools that is loaded when you run EnvyNG.

---

