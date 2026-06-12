---
title: "Finally...External Monitor on Laptop Working"
date: 2006-02-16
forum: Hardware &amp; Laptops
---

### Post by Ominx on 2006-02-16
First post, but I've been lurking for some time now reading countless posts and how-tos trying to configure my Ubuntu setup. I want to say Ubuntu is great and is now running smoothly just as I want it.

Now to the point of this thread. There are a number of discussions regarding setting up a external monitor with a different resolution on a laptop. Most seemed to end without a proper solution, so I hope to offer it here.

It's actually quite obvious when you think about it...even though it took me two weeks to discover. Here's my scenario. My laptop is running at 1280x768 widescreen on a Intel Corporation 82852/855GM Integrated Graphics Device. My external monitor runs at 1280x1024. I only wanted to mirror the display at the higher resolution on the external monitor. The laptop lid is shut. No matter what I added to /etc/X11/xorg.conf, and no matter how many times I reconfigured xserver, 1280x1024 wouldn't stick when X started. The highest resolution was stuck at 1280x768.

So here's what to do.

Run dpkg-reconfigure xserver-xorg and here's the most important part...**YOU MUST HAVE ONLY THE EXTERNAL MONITOR ACTIVE** when you let it autodetect resolution. When you get to the part where you have to select resolutions for x to use, only select the highest resolution of your external monitor. Then select medium and select your monitor resolution with the correct refresh rate.

Once that is completed. Go to this website [http://www.dkfz-heidelberg.de/spec/linux/modeline/](http://www.dkfz-heidelberg.de/spec/linux/modeline/) and find the modeline for only the external monitor. Then sudo gedit /etc/X11/xorg.conf and add this modeline under the monitor section. I deleted the refresh rates already there, because I believe modeline takes care of that and is more accurate than the generated range. Save and close.

Once that is completed, reboot. Again, here's the part I was missing everytime. When you are at the bootloader screen, whether it's grub or ntloader, activate **only** your external monitor now...leaving your laptop lcd blank. If you wait until after X loads, there is no shot you will have your external monitor's resolution available to you. You should be able to activate you external monitor by using some combination of F keys. Mine was FN+F4.

That's really it. Once X starts you should now have booted to you external monitors optimal resolution. 

I hope this helps some of you out there.

Ominx.

---

### Post by wanger123 on 2006-03-29
Hi Ominx, could you post your /etc/X11/xorg.conf file please?

thanks
wanger

---

### Post by mattengland on 2006-05-06
[QUOTE=wanger123]Hi Ominx, could you post your /etc/X11/xorg.conf file please?[/QUOTE]

Yes, please post the .conf file.

-Matt

---

### Post by mattengland on 2006-05-06
[QUOTE=Ominx]Run dpkg-reconfigure xserver-xorg and here's the most important part...**YOU MUST HAVE ONLY THE EXTERNAL MONITOR ACTIVE** when you let it autodetect resolution.[/quote]

What exactly does this mean:  "you must have only the external monitor active"?  Does one deactivate the built-in monitor, or something like that?  What command/procedure does on execute to do this?

> Once that is completed, reboot. Again, here's the part I was missing everytime. When you are at the bootloader screen, whether it's grub or ntloader, activate **only** your external monitor now...leaving your laptop lcd blank.

Again, what does this mean?  How does one do this exactly?

I'm an experienced unix/linux sysadmin and programmer, but I am an Ubuntu newbie, and I'm trying to install on my Thinkpad T41 with an dock/port and an external monitor.   I can get the external monitor to work, but not with the proper resolution/settings (for either Dapper or Breezy).

Thanks for any help,
-Matt

---

