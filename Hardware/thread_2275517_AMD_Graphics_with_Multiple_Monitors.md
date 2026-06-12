---
title: "AMD Graphics with Multiple Monitors"
date: 2015-04-26
forum: Hardware
---

### Post by thomaszimmerman93 on 2015-04-26
I have two graphics cards in my computer and I'm having trouble getting them to play nicely with my 4 monitors. Before upgrading to Ubuntu 15.04 from 14.10, I had all 4 working together nicely, though performance was dismal. All 4 of them could be enabled at the same time, too. 


    > lspci | grep "VGA"                                                 
    01:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Cypress PRO [Radeon HD 5850]
    05:00.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV620 LE [Radeon HD 3450]


The 5850 is connected via DVI to two monitors and a TV. And the 3450 is connected to a third monitor. Choosing the X.Org X Server driver in Additional Drivers is very broken. Only one monitor is detected, Ubuntu says that it is a laptop display, and it has a low resolutions. Choosing the fglrx and fglrx-updates in Additional Drivers both react the same way as each other. Only the devices that are connected to the 5850 are detected and only 2 of them can be enabled at once. Attempting to enable the third device returns the following error: 


    > The selected configuration for displays could not be applied
    could not set the configuration for CRTC 112
   
    Failed to apply configuration: %s
    GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code2: could not set the configuration for CRTC 112


I tried to purge and uninstall the fglrx and fglrx-core and reinstall them from the AMD website but I'm not sure if I did it properly. They failed half way through and the .log file was vague. Upon restarting, graphics didn't work at all and I had to uninstall them from the console, reboot, and restore from my TimeShift Rsync backup. 

Some other bugs that are occurring that I'm assuming are related to graphics:

 - I can't open Chrome without creating two instances of it. If I simply open one, it will sit in my Windows list and I clicking on it does nothing. Opening a second instance allows me to open the first and then I can freely close the second.
 - My Ctrl+Alt+F1/F6 TTYs are just blank screens. I can still log in and issue commands but no text appears or anything. 
 - When I boot to the login screen, I get the could not set the configuration for CRTC 112 error and have to clear the message box before I can log in.
 - Occasionally there are random graphics errors with programs. Spotify panes occasionally just turn blue until I click into the program and Chrome occasionally bugs out and has massive graphical mismatching errors until I kill the process and restart it.

At this point, I'm not really sure how I should proceed. Do you guys have any ideas?

---

### Post by QIII on 2015-04-26
Were I you, I would uninstall the driver.

Part of the problem here is that your HD 3xxx no longer has Linux driver support from AMD.  No version of the proprietary driver suitable for the HD 3xxx will work any longer with the current X Server.

Get it uninstalled, and we can work on getting things going with the Open Source driver, which is pretty good, but it does fall short of the proprietary driver sometimes.

---

### Post by thomaszimmerman93 on 2015-04-26
I see, I was using the Open Source drive in 14.10 when all four were working. Though things like dragging windows performed very poorly. However, I could run Pillars of Eternity on one screen at 60FPS with no issues. So yeah, it was strange.

Anyway, to properly uninstall, should I simply switch over to the open source driver, reboot, and then $sudo apt-get remove fglrx

I tried doing this once but I don't think I did it properly. So I just want to make sure.

---

