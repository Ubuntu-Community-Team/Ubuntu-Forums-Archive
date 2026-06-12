---
title: "Can't get a working xorg configuration for my monitor"
date: 2007-03-04
forum: Hardware &amp; Laptops
---

### Post by MrFlibble on 2007-03-04
Hi all, hope you might be able to help.

I'm having a bit of a one-man Ubuntu Install-fest.  I've got 20 PCs that have been donated by a local company, and I'm installing Ubuntu ready for them to be shipped out to a project in Kosovo.

I've managed 8 machines so far (the installation runs really easily!), but I've run out of monitors that I'm able to get working.

I've got a load of Compaq 472P monitors, which are rather old.  Some searching around on the web suggests that they are capable of 800x600 at a refresh rate of approx. 55-60 Hz.

After the first post-install reboot, the monitor doesn't display anything.  I've tried swapping for a relatively high-spec Sun monitor to see the signal, and it can't display the picture either, measuring it at 103 KHz horizontal, and 163 Hz vertical.

I do the following to the /etc/X11/xorg.conf file:

[list][*]Remove all resolutions except 800x600, and renamed "800x600" to something else to stop it being confused with the predefined 800x600 modes
[*]Add a "Modes" section containing the output of 'gtf' for 800x600 @ 55 Hz
[*]Add a "UseModes" line
[*]Add HorizSync and VertRefresh lines
[*]Remove the lines which load the ddc and i2c modules
[*]Set the NODDC option
[/list]

This gives a picture that my Sun monitor can display, but the Compaq ones can't.  My Sun monitor measures it at 86 Hz refresh rate, despite the fact that I have a VertRefresh line constraining it to a maximum of 60 Hz.  Horizontal Sync is measured at 53 kHz which is also out of my prescribed range.

I have tried running ```
dpkg-reconfigure xserver-xorg
```, but that doesn't produce a working configuration either.

I've checked the /var/log/Xorg.0.log, and it's not throwing my modeline away.  When listing my mode, it puts an asterisk before "Mode".  Does anyone know what that means?  Does anyone know how I can tell which modeline thinks that it's using, as I can't see anything obvious in the log.

The video card has a Matrox MGA G100 [Productiva] AGP chipset.

I'd be grateful for any help you could give, as I really don't want to have to source another load of monitors.

Most importantly, why is X completely ignoring my VertRefresh and HorizSync constraints?  The log states the VR and HS values for my modeline, and they are within my constraint boundaries.

I'm using Ubuntu 6.10 (Alternate).

---

### Post by solar george on 2007-03-04
You've probably already tried this, but 
[http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=1016799&admit=-682735245+1173031892739+28353475]("http://forums1.itrc.hp.com/service/forums/questionanswer.do?threadId=1016799&admit=-682735245+1173031892739+28353475")

---

### Post by MrFlibble on 2007-03-04
Thanks for the reply, but yes, I've seen that.

Some more info - I've booted one of the machines into Windows 95 (which is what is/was installed on the machines before I put Ubuntu on), and worked out that I can run the monitor at 800x600 @ 60 Hz.  My Sun monitor agrees that that is the frequency being supplied, so it's not the Sun monitor mis-measuring.

So, the question is - why does X produce a refresh rate of 86 Hz when it's constrained to run at no more than 60 Hz?

---

### Post by solar george on 2007-03-07
What graphics card do you have?

---

### Post by MrFlibble on 2007-03-08
It's a Matrox MGA G100 [Productiva] AGP.

---

### Post by solar george on 2007-03-08
Try [debian testing]("http://www.debian.org"), if that works copy the xorg config to a usb disk and try it on an ubuntu machine.

---

### Post by MrFlibble on 2007-03-09
Hmm.

I tried installing Debian Testing.  It worked on the monitor first time.  Output is 800x600 @ 61 Hz.

I copied the xorg.conf across to an Ubuntu 6.10 machine with the same model of graphics card and exactly the same monitor, and I get 800x600 @ 81 Hz, which the monitor can't display.

---

### Post by MrFlibble on 2007-03-11
I think I've fixed it.

I diffed the two Xorg.0.log files, and the main difference was the version of the mga module (1.4.1 under Ubuntu vs 1.4.4 under Debian Testing).  I did a forced install of the Debian Testing version of xserver-xorg-video-mga, and now I'm getting the correct refresh rate.

Therefore I'm concluding that it's a bug in 1.4.1 of the mga module.  I've filed a bug report in launchpad.

Thanks for the help, particularly the suggestion to try Debian Testing, as that's what led me to the fix.

---

