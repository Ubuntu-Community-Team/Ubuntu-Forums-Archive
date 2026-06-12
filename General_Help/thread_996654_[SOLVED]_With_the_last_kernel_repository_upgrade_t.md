---
title: "[SOLVED] With the last kernel repository upgrade the nvidia X won't start"
date: 2008-11-29
forum: General Help
---

### Post by siddartha on 2008-11-29
Upgrading the kernel via synaptic and surprise! The x server doesn't start. Going back to boot and using the older kernel works ok. It's the first time in a long time with the standard upgrade breaking things.

What would be the solution?

---

### Post by siddartha on 2008-11-29
The upgrade was from 2.6.27.7 to 2.6.27.9

---

### Post by wd5gnr on 2008-11-29
You need to reinstall the Nvidia driver from a console. This will let it rebuild the kernel modules necessary.

---

### Post by siddartha on 2008-11-30
But I don't have the .run file you get from downloading the driver pack from the nvidia site - only the packages I get from the repositories.

---

### Post by drs305 on 2008-11-30
Reboot to the recovery mode and try xfix? 

If you can get to the desktop in any manner, you might go to System, Administration, Hardware Drivers to see if the nvidia driver is listed and activated? Mine did it automatically on the upgrade to -9 but you might check it anyway.

---

### Post by siddartha on 2008-11-30
Wow! It partially works. So I can get via this recovery mode fix into the graphical interface. The resolution is right, but the fonts and all lines look really bad (LCD display). Now, when I try to do the hardware update it doesn't work. I was going with nvidia 177. No result. I downgraded to 173... it did some installing and in the end still no result.

It keeps saying something about not finding a suitable framebuffer, yet it should run with the accelerated driver so why the framebuffer?

And it is getting worse - I was able to boot the older kernel in order to get in. It was just a hassle to pay attention at startup to pres ESC at grub. Now that doesn't work either - same error.

The only thing I see to blame here is the multiple upgrades - I can't really understand a thing from all these full-automatic processes. It used to be a X config file. Now it says something about not needing one as HAL would take care. HAL has no idea what is going on and for me there's only a long line of questions - why framebufer? Is it with the free nv driver or the proprietary nvidia driver?

I get a fail when it comes to the dell kernel tool. What is that? How does it work? The miracle of magic! Now everything is automated just like Windows, and just like Windows nobody knows a thing and the net is filled with blog posts by imbecils doing a copy-paste of the same issues over and over again.

I'm sick of it.

---

### Post by siddartha on 2008-11-30
Ain't that a beauty? The only mode I can get after long tries is low res. And the wonderful tool of hardware drivers (lame python hack) lists three drivers but none getts activated. To make things even worse, the bar that should display the evolution of the install is meaningless - the whole download goes in the background showing just 0%. More - there's no sign of what is going wrong. Is this the end of Linux? Just a crappy rip off Windows? At least in Windows the drivers now are installed well.

---

### Post by siddartha on 2008-11-30
It's getting worse by the minute. This whole distro is just a terrible mess where you should pray it works out of the box and nothing more.

So the nvidia-common package was not installed. Not that is seems to make any difference. Trying to start the Nvidia server config from the settings prompted that I should use ```
nvidia-xconfig
``` which is installed and working. It will thow up some text about not finding a default keyboard or mouse and make some changes.

dkms autoa installation service for kernel fails again and again prompting for the same crap with the framebuffer.

After doing so many restarts hoping that at some point it would work I discovered that I am losing half of the boot time with a "configuring network devices".

---

### Post by siddartha on 2008-11-30
This surely is a nightmare. So I get the dmesg and the X log from the last boot and I find out that the Linux forum can't say what a file is unless there is an extension. Cool. Back to the DOS days. So I put a .txt extension and I find out that they are too large for this DOS forum... so here they are in a bzipped form.

Edit: removed the logs as they are now useless.

---

### Post by siddartha on 2008-12-01
Solved. At the end of a serie of events that gave no warning this was the result - no driver available.

I was struck by the idea that changing the current driver with an older one broke the previous installed kernel as well. I have checked and gcc was removed - with a good intention, after all this is a graphics machine and not a development one and all the packages are binary.

[LIST]
[*]Uninstalling gcc gave no warning
[*]dkms also said nothing about the lack of gcc
[*]The startup scripts only showed dkms [fail] and no other explanation
[*]"Hardware Drivers" gives no error (far worse than most Windows apps). It eithers works or it doesn't
[*]Installing envy-ng-gtk lead to the surpise to find out that THERE IS NO gtk port
[*]envy-ng started with the gtk option starts envy-ng-qt, but that is no requirement on install
[*]envy-ng goes down the same road of downloading and installing something without giving a reason, a report, a visible log or a reason for its failure
[*]nvidia-kernel-common said in its description that is common and needed by all nvidia drivers, yet it can be uninstalled without any warning
[*]On the other hand, smart dimmer which works only with one type of nvidia card which is only for laptops will cause at uninstall the uninstallation of acpi-support and powermanagement-interface as well. And it is useless for those with a different card.
[*]The name of the Hardware Drives is actually Jockey
[/LIST]

That being said - reinstalling the missing packages by guessing would solve the problem with a reboot.

---

