---
title: "Nvidia - Fed up with it!!"
date: 2010-03-15
forum: Hardware
---

### Post by emoguitarist06 on 2010-03-15
I have a Compaq Presario CQ50 110-US Notebook with Nvidia Geforce 8200M graphics
I'm running 32 Ubuntu Karmic

I have tried the Nvidia Driver version 190.53 & version 195.3Beta
and my screen still constantly flickers!
It flickers when turning the laptop on, off, when watching movies, when browsing the web, and when it's just sitting there doing nothing!

Please help! I feel like punching my computer screen
I very much dislike Windows but I never had this problem with it :(


**Please Help**

---

### Post by Goveynetcom on 2010-03-16
Have you tried seeing if anyone has had luck with your card? Do some googling and post back...

---

### Post by prshah on 2010-03-16
> **emoguitarist06 said:**
> my screen still constantly flickers!
It flickers when turning the laptop on, off,

It doesn't seem to me to be a software problem, more likely to be a hardware issue; here's how you can check:

a) If you still have Windows, please boot into it. Wait for things to settle down, then try moving the lid back and forth (only a few degrees, and slowly) and check for a flicker.

b) If you dont have windows (or as a secondary check) boot to either the BIOS screen or the GRUB menu, and move the lid back and forth and check for a flicker. At this point, Ubuntu is not running, and any flicker here will be indicative of a hardware problem.

c) Check with a live CD; this will use the VESA driver and not the nvidia driver; this will help eliminate either Ubuntu or Nvidia.

d) Check your refresh rates in the nvidia control panel. Most laptops have a standard refresh rate of 60Hz; check your manual for the exact. Also check if you are running at the optimal (aka native) resolution for your model.

Please post back with results.

---

### Post by emoguitarist06 on 2010-03-16
> **prshah said:**
> It doesn't seem to me to be a software problem, more likely to be a hardware issue; here's how you can check:

a) If you still have Windows, please boot into it. Wait for things to settle down, then try moving the lid back and forth (only a few degrees, and slowly) and check for a flicker.

b) If you dont have windows (or as a secondary check) boot to either the BIOS screen or the GRUB menu, and move the lid back and forth and check for a flicker. At this point, Ubuntu is not running, and any flicker here will be indicative of a hardware problem.

c) Check with a live CD; this will use the VESA driver and not the nvidia driver; this will help eliminate either Ubuntu or Nvidia.

d) Check your refresh rates in the nvidia control panel. Most laptops have a standard refresh rate of 60Hz; check your manual for the exact. Also check if you are running at the optimal (aka native) resolution for your model.

Please post back with results.

Thanks for the advice! I found out it's not a hardware issue... I reinstalled the driver and messed around for he NVIDIA control panel and so far so good... i'll let you know if I begin having issue again

---

### Post by emoguitarist06 on 2010-03-17
> **prshah said:**
> It doesn't seem to me to be a software problem, more likely to be a hardware issue; here's how you can check:

a) If you still have Windows, please boot into it. Wait for things to settle down, then try moving the lid back and forth (only a few degrees, and slowly) and check for a flicker.

b) If you dont have windows (or as a secondary check) boot to either the BIOS screen or the GRUB menu, and move the lid back and forth and check for a flicker. At this point, Ubuntu is not running, and any flicker here will be indicative of a hardware problem.

c) Check with a live CD; this will use the VESA driver and not the nvidia driver; this will help eliminate either Ubuntu or Nvidia.

d) Check your refresh rates in the nvidia control panel. Most laptops have a standard refresh rate of 60Hz; check your manual for the exact. Also check if you are running at the optimal (aka native) resolution for your model.

Please post back with results.

OK please ignore my past post. What I did was "Sudo apt-get purge nvidia*" and then reinstalled nvidia beta driver 195.30 and eventually it began flickering again

It's not a hardware issue because it doesn't flicker in the bios and only when ubuntu is running

I no longer have windows

Right now I'm running he live cd of ubuntu and it's working great but it asked me if I wanted to enable nvidia restricted drivers SHOULD I?
I want to because I want to be able to use compiz

---

### Post by coffeecat on 2010-03-17
Are you running Karmic? Because, if so, the latest version of the nvidia driver in the Ubuntu repositories is 185. Most people have no problems with this. I presume you must have installed the driver from a download from nvidia. Was there a reason for this? Have you tried letting System > Administration > Hardware Drivers install the 185 version for you?

If you install the proprietary driver in a live session with jockey (Hardware Drivers utility) you will lose it as soon as you reboot, and since you have to reboot to activate it, then the answer to your last question is... no.

---

### Post by emoguitarist06 on 2010-05-05
UPDATE

My laptop was just crapping out
It was a hardware problem
I sold it
and now I have an Asus EeePC 1201N which I am in LOVE WITH!!
Thanks guys for all of your input, help, and advice

HAPPY *BUNTUING!!

---

