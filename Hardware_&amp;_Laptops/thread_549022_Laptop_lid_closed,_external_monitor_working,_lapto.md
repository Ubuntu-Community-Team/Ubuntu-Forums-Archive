---
title: "Laptop lid closed, external monitor working, laptop LCD STILL ON?!?!"
date: 2007-09-12
forum: Hardware &amp; Laptops
---

### Post by kraigory on 2007-09-12
Alright, so i've got a Dell Inspiron E1505 running Feisty, and I've got a flat panel monitor hooked up to the monitor port on the back.

When I close my laptop lid, both screens go blank. Then, when I move the mouse around, both screens (the external monitor, and the laptop's lcd, which i can see bright up through the cracks) turn on. The external monitor works fine. 

So, is there any way I can get the laptop's screen to turn off when the lid is closed, but STAY off when the external monitor comes on due to mouse movement? I guess it's not all that big of a deal, but i'm pretty much ALWAYS using the external monitor, and i'd feel alot better about leaving the laptop booted for long periods of time if the lcd wasn't chugging along, using energy and generating a little extra heat that i sure don't need.

Any ideas? Thanks!


*note, i did not buy this laptop with ubuntu on it. I installed it myself, with dual-boot.

---

### Post by kraigory on 2007-09-12
Also note, the lcd does turn off in xp when the lid is shut, so it's not a hardware problem.

---

### Post by wieman01 on 2007-09-13
I'd be interested in finding a solution as well. I have the same problem which I noticed a while ago, however, I presumed there is no solution at the moment. Perhaps there is after all.

---

### Post by frith on 2007-09-13
I have had similar experiences, and my final conclusion is that the support for laptops and external monitors just isn't really that good.

In my case, when I connect the monitor before turning on the laptop, it diverts everything to the external display and keeps the backlight of the laptop off. But if I do something like enable TwinView and look really closely at the laptop I can see the mouse moving on the screen, just the backlight is off.

I believe there might be a solution in the nVidia binary drivers, (assuming you have an nVidia card...) if you do sudo nvidia-settings you can enable or disable displays. I'm pretty confident there would be a way to turn off the internal display when closing the lid, but it sounds like you have a clone situation going on - what happens to the internal display happens to both. Given that we are talking about software which has readily available source code, I'd be surprised there isn't something you could do to rectify the situation, the real question is "how much effort are you willing to expend getting this to work" :)

A good start might be a google/forum search on the subject...

Frith.

---

### Post by wieman01 on 2007-09-13
External video support isn't the best I have seen, but much better than it used to be. Dapper's video support was horrible.

---

### Post by hardyn on 2007-09-13
got a similar problem, lid switch works first time, but not after subsequent closes... but the Fn button combination does suspend the machine

this is a new thing for me, so i guess one of the many updates has broken it?

YES YES YES... laptop support in linux needs a serious kick in the back side, im not sure what is lacking? maybe serious kernel overhaul?  mabe somebody more familliar with the linux nuts and bolts could shed some light?

---

### Post by frith on 2007-09-13
I think its more a case of prioritising. Up until now everyone has been spending time on just getting various drivers to work at all. But it seems that now the system is working pretty well on most computers, the developer types can start focusing on 'features'. I'm quite sure we will see leaps and bounds in monitor support over the next 12 months. IMHO its the last big issue with Ubuntu on laptops...

Frith.

---

### Post by aaaantoine on 2007-09-13
If your laptop has a switch to toggle the backlight (like mine has), you can press that before you close the lid.

It doesn't eliminate the signal to the screen, but it'll save some energy at least.

---

### Post by kraigory on 2007-09-13
yeah mine doesn't have that. i'm thinking about upgrading to gutsy? Any chance that it'll help?

---

### Post by wieman01 on 2007-09-14
> **frith said:**
> I think its more a case of prioritising. Up until now everyone has been spending time on just getting various drivers to work at all. But it seems that now the system is working pretty well on most computers, the developer types can start focusing on 'features'. I'm quite sure we will see leaps and bounds in monitor support over the next 12 months. IMHO its the last big issue with Ubuntu on laptops...

Frith.
That is indeed true. It has made great progress.

---

### Post by Nilelith on 2007-09-14
Yer would love a fix to this, i have them same problem

---

### Post by GoodPanos on 2007-09-25
Same here.  I have a Dell Latitude D420 and after a while it gets real toasty when I have the lid closed with an external monitor.

Any advice would be greatly appreciated.

---

### Post by GoodPanos on 2007-09-27
Bum.  I am really looking forward to a solution on this. 8-[

Currently, when docking the notebook I have to leave the LCD open so it does not overheat, but the LCD remains lit and it just waists energy...

---

### Post by wieman01 on 2007-09-27
> **GoodPanos said:**
> Bum.  I am really looking forward to a solution on this. 8-[

Currently, when docking the notebook I have to leave the LCD open so it does not overheat, but the LCD remains lit and it just waists energy...
Perhaps we need to wait until Gutsy comes out.

---

### Post by GoodPanos on 2007-09-27
Probably so...

Has any one tried it with any of the beta releases?

---

### Post by mezcla on 2007-09-27
I am having similar problems, but I can't get the external monitor to display the image correctly. If I could at least fix that I'd be happy.  Here goes:

I am running Feisty 32-bit on a Dell Inspiron 1100.  I am connecting to a Dell 3300MP LCD projector.  In windows I hit Fn + F8 and voila the image is on both screens.  When I try that in Ubuntu the image goes to the projector but is shifted about an inch down with a lot of static up top.  I have to hit the button combo again to get the image on my laptop screen again but it stays messed up.  My mouse pointer still works and I have to click an inch above everything to navigate.  It took me a little while to get this thing running in a resolution other than 600x480 so I should have expected video troubles, but I am willing to work at this if anyone has suggestions.

My video card is using the i810 driver so I was thinking of trying to switch to the intel driver but was unaware if I would need to & unsure how to edit xorg.conf.  (don't worry it's backed up).  Thanks in advance for any suggestions.

---

### Post by wieman01 on 2007-09-27
> **mezcla said:**
> I am having similar problems, but I can't get the external monitor to display the image correctly. If I could at least fix that I'd be happy.  Here goes:

I am running Feisty 32-bit on a Dell Inspiron 1100.  I am connecting to a Dell 3300MP LCD projector.  In windows I hit Fn + F8 and voila the image is on both screens.  When I try that in Ubuntu the image goes to the projector but is shifted about an inch down with a lot of static up top.  I have to hit the button combo again to get the image on my laptop screen again but it stays messed up.  My mouse pointer still works and I have to click an inch above everything to navigate.  It took me a little while to get this thing running in a resolution other than 600x480 so I should have expected video troubles, but I am willing to work at this if anyone has suggestions.

My video card is using the i810 driver so I was thinking of trying to switch to the intel driver but was unaware if I would need to & unsure how to edit xorg.conf.  (don't worry it's backed up).  Thanks in advance for any suggestions.
This one might be worth taking a look at:

[http://ubuntuforums.org/showthread.php?t=411674]("http://ubuntuforums.org/showthread.php?t=411674")

---

### Post by mezcla on 2007-09-27
Wieman, thanks for the link!!!  I love that the projector is called a beamer, I've never heard that before.:)

---

### Post by wieman01 on 2007-09-27
> **mezcla said:**
> Wieman, thanks for the link!!!  I love that the projector is called a beamer, I've never heard that before.:)
He is NOT talking about a BMW though. ;-) Yes, that's German English as it appears.

---

### Post by balthamaisteri on 2007-10-17
I have this same problem, i've fixed it couples of time.

I just needed to add something in xorg.con to fix it, but this time even that did not help :/ i don't know what i did wrong, now i just use this script that is on my desktop to poweroff my monitor.

Hope that Gutsy works.

---

### Post by GoodPanos on 2007-10-27
Well, Gutsy is finally here.  Has any one tried it?

It works on another laptop I have, but then again that laptop has an nVidia graphics card.  I am more interested to see it work on an Intel graphics card (GMA 950).  It will be a while before I upgrade that laptop to Gutsy.

Until then I look forward to seeing any of your findings.  ;-)

---

### Post by Dirk_McJerk on 2007-11-05
When I boot up my computer right as the grub screen comes up I press Fn F8 to toggle to my external monitor and close my laptob lid. This works for me.

---

### Post by GoodPanos on 2007-12-08
Things are finally working great.  However, I am not sure if it's really Gutsy the fix.

I connect my Dell laptop to a docking station.  The docking station supports both DVI and VGA outputs.  The docking station was connected to my KVI via the VGA.  When I had this setup  the laptop would not support the native resolution of the monitor (1680x1050) and it looked horrible but some how the laptop screen would shut off.

Then I connected the docking station directly to the monitor via DVI and now all works great; monitor is at native resolution (so crispy) and laptop screen shuts off.  Is it the DVI or Gutsy?  I don't know for sure.

:)

---

### Post by allenb on 2007-12-10
I am using Gutsy on an HP/Compaq NW8440 and I use a docking station with external monitor/keyboard/mouse.  When I close the lid, the laptop screen turns off as expected, and the external monitor remains in use.  I can move my USB mouse around and the laptop screen remains powered off, however my PS/2 keyboard will not work if the laptop lid is closed :(  I have tried messing around with xorg.conf to see if I could turn the laptop display off without closing the lid (thus allowing use of my keyboard), but I have had no success.  This machine uses an ATI FireGL graphics card which requires the ATI proprietary drivers to work correctly, so I don't have all the configuration options that nVidia users have.

---

