---
title: "My laptop has not successfully resumed from closing the lid in over 2 years"
date: 2014-12-10
forum: Hardware
---

### Post by 7-webmaster on 2014-12-10
I am extremely frustrated.  I have been reporting that my laptop does not successfully resume after the lid is opened ever since Ubuntu 12.4.  I am now up to Ubuntu 14.10 plus the 3.18-rc6 development kernel, and my system STILL will not resume after opening the lid.  That is well over two years of having a laptop which is effectively a desktop because I cannot take it anywhere, since transporting it requires closing the lid, which I cannot do!  I have to leave my mouse sitting on the keyboard so the lid will not accidentally close from the effect of gravity!  I have reported this over and over and over again on each successive release and still nobody will offer me any assistance.  I cannot afford to go out and buy a new laptop, and in any event the newer the laptop the more likely it is that LINUX will not support it.  This is a three-year old laptop from Dell, a well-respected manufacturer with VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6620G].  I have upgraded the microcode to the latest level A06.  I have upgraded the kernel to the latest development level, and still I am expected to jump through poorly documented hurdles which I do not understand.  I have tried both the recommended X.org driver and the proprietary fglrx driver, with no difference in behavior.  I have repeatedly asked the X.org group for a command that I can issue to turn on the back-light on  my display, since that is the only reason the system is not usable after opening the lid.  They tell me to change the brightness setting!  The laptop is actually running after the lid is opened:  I can ssh, ftp, and http into is.  The mouse is turned on, but I cannot see what it is pointing at.  The keyboard is working but all I can do is issue the Alt-PrtScrn-RSEIUB commands to reboot from scratch, throwing all of my work away, and taking a relatively long time to get the system operational again.

Two years is far too long for me to have been forced to put up with a non-operational system.  Would someone please explain to me what I have to do to get this system working?

---

### Post by TheFu on 2014-12-11
Do you have links to the launchpad bug reports for each issue?
That is the bug tracking system for Ubuntu, not these forums.

It would be helpful if you provided more exact data on what you've tried (i.e. what system setting changes you've made to correct this) and details about your system.  For example, did you modify anything in /etc/systemd/logind.conf?  Are you trying to suspend or hibernate? How much RAM and what size is the swap partition?
Does manually running the **pm-suspend** command work or not?
What do the system log files show? Anything funny? Any warnings or errors?

Reading your post, I can see the frustration.  It can be tough.  It is best to post about 1 issue at a time here.  Just 1.  Lets try to tackle the sleep stuff - since I don't have a backlight on any of my systems.

Oh - and the exact model of Dell might be helpful in the title, so that other people with that model might see the issue, recall how they fixed it and post a solution.  I have a few Dell laptops - 1535 and 1558, but always set them to NEVER sleep or hibernate based on the lid closing. If I travel, I want the encrypted storage completely powered off for security reasons - but that is me. Reboots only take 20-30 sec for my machine - not a big deal.  OTOH, I don't really reboot more than once a month.

BTW, I don't run stock Ubuntu GUI, so any point-n-click stuff I can't really help with, but if you are willing to try shell commands to get this working, I'm happy to try and help. Otherwise, say something and hopefully someone else will come.

---

### Post by 7-webmaster on 2014-12-11
> **TheFu said:**
> Do you have links to the launchpad bug reports for each issue?
That is the bug tracking system for Ubuntu, not these forums.

It would be helpful if you provided more exact data on what you've tried (i.e. what system setting changes you've made to correct this) and details about your system.  For example, did you modify anything in /etc/systemd/logind.conf?  Are you trying to suspend or hibernate? How much RAM and what size is the swap partition?
Does manually running the **pm-suspend** command work or not?
What do the system log files show? Anything funny? Any warnings or errors?

Reading your post, I can see the frustration.  It can be tough.  It is best to post about 1 issue at a time here.  Just 1.  Lets try to tackle the sleep stuff - since I don't have a backlight on any of my systems.

Oh - and the exact model of Dell might be helpful in the title, so that other people with that model might see the issue, recall how they fixed it and post a solution.  I have a few Dell laptops - 1535 and 1558, but always set them to NEVER sleep or hibernate based on the lid closing. If I travel, I want the encrypted storage completely powered off for security reasons - but that is me. Reboots only take 20-30 sec for my machine - not a big deal.  OTOH, I don't really reboot more than once a month.

BTW, I don't run stock Ubuntu GUI, so any point-n-click stuff I can't really help with, but if you are willing to try shell commands to get this working, I'm happy to try and help. Otherwise, say something and hopefully someone else will come.

The latest report on launchpad is 
[https://bugs.launchpad.net/bugs/1392460](https://bugs.launchpad.net/bugs/1392460)

The system has 6GB of RAM and a 6GB swap.

One of the problems I have had communicating with the support teams is that I just let the Ubuntu configurator set everything up.  I have not modified anything except the Apache server config.  I was asked to try the 3.18 kernel, but it took me two weeks to get it going because I was not explicitly warned to manually remove all of the proprietary drivers that Ubuntu 14.10 installed to support some of the hardware first.  I didn't know what fglrx or bcmwl referred to when the install of the 3.18 kernel failed because I hadn't installed them, the Ubuntu configurator had.

The system log files, in particular dmesg show everything is hunky dory.  The kernel is unaware of the fact that the backlight was not turned on because it doesn't know to check for that.

The point of a laptop is its portability.  If I power off every time I close the lid, then it is not the few seconds spent rebooting that is the issue, it is the several minutes it takes to manually get back to whatever point I was in my work flow at the time I had to shut the laptop.  Some tools, for example LibreOffice and gedit, will reopen the documents I was working on at the point where I was when they were last saved, but most, for example gvim, do not.  Since I mostly use this laptop for web development I would waste a lot of time getting back to where I was, and before closing the lid I would have to write myself extensive notes to remind myself of exactly what I was doing at the point I shut down.

Prior to kernel 3.16, which is used in Ubuntu 14.10, suspend and resume were very iffy on this hardware.  I would close the lid and the laptop would remain powered on some times, overheating in my briefcase and draining the battery.  If it did suspend I would open the lid and the laptop would resume, some times, and if it did resume it would turn on the backlight, some times.

Starting with kernel 3.16 suspend and resume are entirely reliable.  Every time I close the lid the system suspends.  Every time I open the lid the system resumes.  However the failure to turn on the backlight is now 100% consistent.  The backlight is NEVER turned on.  It is nice that kernel 3.16 is 100% consistent in its behavior in this respect since it was frustrating to never know what the laptop would do each time I opened it up.  After opening the lid the system responds to keyboard input, but I cannot see the results of that keyboard input because the backlight is off.  Because the keyboard is working I can now restart the system using Alt-PrtScrn-RSEIUB where in the past about half the time I had to cycle the power button.  The Microsoft USB mouse is activated, but I cannot see the results of mouse operations because the backlight is off.  The system is running properly because I can use ssh, ftp, and http to access the system from another computer.  But I cannot see the results of anything because the backlight is off.

If I use the proprietary fglrx driver I can manually suspend and resume the system, as long as I do not close the lid of the laptop.  If I do use the proprietary driver however on resume the backlight is not turned on.  Moreover the proprietary driver has some functional limitations.  The X.org driver which is used by default is much more functional, but does not turn on the backlight when I manually resume.  The X.org driver had some minor functionality problems back in Ubuntu 13.4 that resulted in strange display artefacts, but those are all resolved in 14.10.  I asked the X.org project how to manually turn on the backlight and the response was "The driver should turn on the backlight."  Since the driver doesn't turn on the backlight that is an annoying response.

The laptop is a Dell Vostro 3555.  Most of the systems in the Dell Vostro 3500 series run Intel processors with Nvidia graphics, so this one is the odd man out using an AMD processor and AMD/ATI graphics.

---

### Post by 7-webmaster on 2015-07-10
Just to close this issue my Dell Vostro 3555 laptop now resumes (mostly) on Vivid Vervet (15.04).  The main problem, that the display was not turned on, is resolved although every so often on resume the USB ports are dead and the network manager icon does not work and I cannot connect to wi-fi, although the Ethernet port works.

---

### Post by john409 on 2015-07-10
Should you mark this one as resolved then?

---

### Post by Bucky Ball on 2015-07-10
As it's been woken from its slumber and is now heading toward other support issues, with the only sign posted of a resolution to this one being the upgraded OS, let's close it. 14.10 runs out of support in a week or so also so anyone with similar issues on 14.10 should upgrade to a supported release (12.04 LTS, 14.04 LTS or 15.04) and see if problems persist. 

*Thread closed.*

Please post a new thread(s) for any new issues. Good luck. :)

---

