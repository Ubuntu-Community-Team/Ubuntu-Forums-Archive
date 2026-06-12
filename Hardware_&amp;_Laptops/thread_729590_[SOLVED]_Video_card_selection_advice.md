---
title: "[SOLVED] Video card selection advice"
date: 2008-03-20
forum: Hardware &amp; Laptops
---

### Post by twin_57103 on 2008-03-20
Hi folks,

I'm working on a new system build to replace one that is quite literally falling apart.  The biggest decision is the video card.  I've been looking at NVIDIA 8600's.  I've seen some mixed results on the forums.  Any advice for or against?  If against, would you suggest an alternative?

My general build goals: dual-boot with Windows Vista (Home premium); light-to-moderate gaming under Windows (nothing high-end).  I'm trying to leave room for expandability without going overboard.  I'm wavering between an Intel dual-core and an AMD Phenom quad core processor (the Intel quad cores are a bit pricey and I don't really *need* that much processor).  Probably 4 Gb RAM (PC6400/800 MHz).  I'll decide on the motherboard once I sort out which processor I want to use.  Looking at around a 600W power supply.

---

### Post by twin_57103 on 2008-03-20
I am still trying to decide on the video card.  Does anyone have any thoughts?

Here's what I settled on for the rest of the build:

Motherboard: ASUS M2N-SLI Deluxe

Processor: AMD Phenom quad-core (2.2 GHz)

Power Supply: 700W Coolmax Green Power

RAM: 4 Gb PC6400 (2x2 Gb; Super-Talent)

Drives: 2x320 Gb hard drives (Hitachi), 2 Lite-on Lightscribe DVD burners

Operating systems: Windows Vista Home Premium and Ubuntu

---

### Post by Existentialist on 2008-03-20
What kind of price are you looking at for the graphics card?  I would recommend the new 9600gt over the 8600 line, and with the release of the new 9800's in the coming weeks, prices on the 8800gt 256 or 512 should be dropping also.

---

### Post by twin_57103 on 2008-03-20
I'm trying to balance cost and performance.  I'd like to stay under $200 (US) at most.  It looks like these cards run right around this point.  Will the performance gain be worth the added cost (I'm assuming yes, otherwise you wouldn't have recommended it)?  This is a bit more than I'd been planning on spending, but I'd rather get the right card now than have to upgrade later.

---

### Post by mdlueck on 2008-03-20
> **twin_57103 said:**
> I've been looking at NVIDIA 8600's.

I think also important is the vendor that puts the nVidia chip on their board. I have had good success with PNY boards, and I understood that PNY has an exclusive agreement with nVidia to produce boards for the Quaddro line of chips.

PNY tends to design their boards without the need for cooling fans - at least the ones I have encountered. "One less thing to go wrong" in my opinion.

To upgrade older systems for use with Ubuntu, I have found good deals on PNY 6200 AGP boards. That particular board is compatible with both 3.3v and 1.5v AGP slots.

---

### Post by twin_57103 on 2008-03-20
> **mdlueck said:**
> I think also important is the vendor that puts the nVidia chip on their board. I have had good success with PNY boards, and I understood that PNY has an exclusive agreement with nVidia to produce boards for the Quaddro line of chips.

PNY tends to design their boards without the need for cooling fans - at least the ones I have encountered. "One less thing to go wrong" in my opinion.

I'll keep that in mind as I'm choosing the new one.

> **mdlueck said:**
> To upgrade older systems for use with Ubuntu, I have found good deals on PNY 6200 AGP boards. That particular board is compatible with both 3.3v and 1.5v AGP slots.

This is a new build, so upgrading isn't a concern.  I didn't want to try to keep my old one running; it's been trouble since day 1.  I do a fair amount of restoration for old systems, including some Ubuntu builds (depending on the end user), and I'll keep that in mind if I need to swap video cards.  Thanks!

---

### Post by Existentialist on 2008-03-21
Best cards for the money right now are the 9600gt's in my opinion.  Good balance between price and performance.  They run $140-160.  The 8800gt's will outperform the 9600's, but they will cost you around $200.  Either of these will be significantly higher performance than the 8600's, so I would go with one of them, but which one is up to you.

---

### Post by zeta on 2008-03-21
Hi twin, 
do you plan to attach a toaster to your pc or why do go for a 600W power supply? I think even 400W would be more then you need. This [calculator]("http://www.extreme.outervision.com/psucalculatorlite.jsp")  gives you a rough estimate how much you need. Also, in case you go or one of these fanless AGPs - I would - you need a very well ventilated case. A 9600Gt runs at around 100W and this power has to go somewhere.

---

### Post by Existentialist on 2008-03-21
> **zeta said:**
> Hi twin, 
do you plan to attach a toaster to your pc or why do go for a 600W power supply? I think even 400W would be more then you need. This [calculator]("http://www.extreme.outervision.com/psucalculatorlite.jsp")  gives you a rough estimate how much you need. Also, in case you go or one of these fanless AGPs - I would - you need a very well ventilated case. A 9600Gt runs at around 100W and this power has to go somewhere.

The 9600gt's have had far fewer heat issues than the 8800gt's did initially, and on average, the 9600gt consumes around 195-200 watts during full 3d acceleration compared the the 8800gt's 220 watts.  Both of these cards recommend a minimum of a 400 watt psu, but the 9600gt recommends 26v on the +12 volt rails, where the 8800gt recommends 22v.  This is the most commonly overlooked part of peoples builds, wattage is often looked at rather than the +12v rail configuration.  Your psu choice may be a little overkill, but it will leave you options for running sli down the road, and if the price isn't too high it should be fine.

---

### Post by twin_57103 on 2008-03-22
In the end, I picked an EVGA GeForce 9600, 512 Mb DDR3.  Thanks for the thoughts!

---

### Post by Existentialist on 2008-03-22
> **twin_57103 said:**
> In the end, I picked an EVGA GeForce 9600, 512 Mb DDR3.  Thanks for the thoughts!

Good choice, I've always liked EVGA.  Make you sure register it over at there website within 30 days for the full lifetime warranty.  You can always step up to a different card with them within 90 days also; some of the best customer service people I have worked with, and a good forum from them also.

---

### Post by twin_57103 on 2008-03-22
> **Existentialist said:**
> Good choice, I've always liked EVGA.  Make you sure register it over at there website within 30 days for the full lifetime warranty.  You can always step up to a different card with them within 90 days also; some of the best customer service people I have worked with, and a good forum from them also.

Good to hear.  I'll be sure to register everything on this system, spam or no.  Thanks for the advice.

---

### Post by twin_57103 on 2008-03-29
Followup...**I highly recommend not attempting to install with this card until 8.04 comes out**.  It does not boot on the live CD's for 7.10 or earlier.  Here is [a post describing the problem]("http://ubuntuforums.org/showthread.php?t=733923").  ATM, I am unable to install Ubuntu; the [alternate CDs will not install either]("http://ubuntuforums.org/showthread.php?t=737670").

This card appears to be supported by 8.04 beta, and I may wait to dual-boot until 8.04 comes out in a final version.

---

### Post by Existentialist on 2008-03-30
> **twin_57103 said:**
> Followup...**I highly recommend not attempting to install with this card until 8.04 comes out**.  It does not boot on the live CD's for 7.10 or earlier.  Here is [a post describing the problem]("http://ubuntuforums.org/showthread.php?t=733923").  ATM, I am unable to install Ubuntu; the [alternate CDs will not install either]("http://ubuntuforums.org/showthread.php?t=737670").

This card appears to be supported by 8.04 beta, and I may wait to dual-boot until 8.04 comes out in a final version.

Sorry, I should have mentioned you would have to use 8.04 or an alternate method to install until you could install the drivers manually.  I had 7.10 installed already when I upgraded to my 8800gts, and 8.04 worked fine when I upgraded so I forgot this could cause issues.  For what it's worth, you still bought the best value card for the money considering nothing over the 8600's would have worked by default for anywhere near that price.

---

### Post by twin_57103 on 2008-03-30
Existentialist,

I couldn't use the alternate CD either; believe me, I tried.  I got "unable to find installable kernel" errors.  My best guess is that something in the rest of the hardware simply isn't compatible with any of the older versions.

Now, I'm trying to install the driver for the card and I'm getting confused.  I found it on [NVIDIA's web site]("http://http://www.nvidia.com/object/linux_display_ia32_171.06.html") through a link on [another thread]("http://http://ubuntuforums.org/showthread.php?t=705795").

I've tried to follow their installation instructions, but apparently it cannot install while X is running.  It also appeared like others weren't necessarily following the same procedure when installing it?  Can you help me get this driver installed?  Thanks!

Removed solved tag since I'm still having a lot of trouble.

---

### Post by Neo0351 on 2008-03-30
> **twin_57103 said:**
> Existentialist,

I couldn't use the alternate CD either; believe me, I tried.  I got "unable to find installable kernel" errors.  My best guess is that something in the rest of the hardware simply isn't compatible with any of the older versions.

Now, I'm trying to install the driver for the card and I'm getting confused.  I found it on [NVIDIA's web site]("http://http://www.nvidia.com/object/linux_display_ia32_171.06.html") through a link on [another thread]("http://http://ubuntuforums.org/showthread.php?t=705795").

I've tried to follow their installation instructions, but apparently it cannot install while X is running.  It also appeared like others weren't necessarily following the same procedure when installing it?  Can you help me get this driver installed?  Thanks!

Removed solved tag since I'm still having a lot of trouble.

twin, I posted how I got my running one this thread [http://ubuntuforums.org/showthread.php?t=705795&highlight=9600gt](http://ubuntuforums.org/showthread.php?t=705795&highlight=9600gt)
post 37, hope this helps

---

### Post by mdlueck on 2008-03-30
> **twin_57103 said:**
> 
I couldn't use the alternate CD either; believe me, I tried.  I got "unable to find installable kernel" errors.  My best guess is that something in the rest of the hardware simply isn't compatible with any of the older versions.

Did you try to install the text mode Ubuntu via the Alternate CD? That worked for me on a Dell Latitude D830 w/ nVidia NVS140 to get Ubuntu 7.04 installed onto it. After getting that far, we installed the entire desktop environment and BEFORE rebooting we configured x.org to use VESA drivers at first, then used Envy to install the nVidia binary drivers.

> **twin_57103 said:**
> 
Now, I'm trying to install the driver for the card and I'm getting confused.  I found it on [NVIDIA's web site]("http://http://www.nvidia.com/object/linux_display_ia32_171.06.html") through a link on [another thread]("http://http://ubuntuforums.org/showthread.php?t=705795").

I *highly* suggest installing nVidia binary drivers with the assistance of Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by Neo0351 on 2008-03-30
> **mdlueck said:**
> Did you try to install the text mode Ubuntu via the Alternate CD? That worked for me on a Dell Latitude D830 w/ nVidia NVS140 to get Ubuntu 7.04 installed onto it. After getting that far, we installed the entire desktop environment and BEFORE rebooting we configured x.org to use VESA drivers at first, then used Envy to install the nVidia binary drivers.



I *highly* suggest installing nVidia binary drivers with the assistance of Envy:
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

envy will not work with the 9600gt.  twin needs to install the 171.06 drivers from nvidia.  my post is how i got my 9600gt to work, no need for a livecd or envy.  and the driver will configure xorg for him for the his video card and screen.

---

### Post by twin_57103 on 2008-03-30
Neo, I'd seen that thread, but it was a little intimidating...thanks for the push to try it myself.  

I've worked my way through your instructions.  I had to add "nv" do the disabled modules in nano /etc/default/linux-restricted-modules-common, but it appears to have installed properly now. I got an NVIDIA splash screen and I can tell the that there is a slight improvement in the display quality.  I've been able to turn on desktop effects, which wouldn't work before.

Thanks for the help!!

---

### Post by Neo0351 on 2008-03-30
no problem, it's really not as hard as some some people make it out to be.  the biggest thing is figuring out what you need and what to disable, i worked for days to get mine running and once i knew what to do, it takes two minutes.

---

### Post by twin_57103 on 2008-03-30
Neo, have you ever hard about sleep/resume issues with this card?  It's unlikely, but I'd like to ask.  At first I though my problems were simply Windows glitches (Vista is known to have sleep/resume problems), but I've had the same problem under Ubuntu.  I didn't let the system go to sleep ever before installing this driver, so I don't know if there is any connection (I doubt it).  When the system powers down, it doesn't resume - the fans come on, but there's no monitor, mouse or keyboard response (including caps lock/num lock).  I'm troubleshooting this problem with the various part vendors, but I figure it's worth asking.  Thanks!

---

### Post by Neo0351 on 2008-03-30
I'm sorry, I have no idea.  I don't put my computer to sleep because it never resumes, like you said, the screen never turns on.  I know I had the problem with my laptop, a Toshiba A65 and when I used my 7300LE in my computer.  I know Linux has problems with sleep and hibernation.

---

### Post by twin_57103 on 2008-03-30
Not a problem - I just figured I'd ask.  Thanks for all the help.

---

### Post by Neo0351 on 2008-03-30
If you figure out what's wrong, let me know, I'm interested to know.  I would like to suspend my computer sometimes, however, it really doesn't matter much now I put a WD Raptor hard drive in.  It boots so fast now it might be pointless to suspend.

---

### Post by twin_57103 on 2008-03-31
If I get anywhere, I'll post it here.  I'm so used to just walking away from the computer that remembering to turn it off is pretty awkward :)

---

### Post by twin_57103 on 2008-04-07
I think I found a workaround.  I disabled S3 sleep in favor of S1.  The standby energy usage will be slightly higher, but so far, it appears to have solved the problem.  Thanks again for all the help!

---

### Post by twin_57103 on 2008-04-08
Apparently the workaround fixed the system resume problem, but not Ubuntu resume.  Windows resumes beautifully.  I've posted it with my [old sleep/resume thread]("http://ubuntuforums.org/showthread.php?t=747547").  Still working on it!

---

