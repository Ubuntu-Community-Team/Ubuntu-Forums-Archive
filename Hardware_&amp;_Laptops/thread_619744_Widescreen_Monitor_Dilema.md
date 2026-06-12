---
title: "Widescreen Monitor Dilema"
date: 2007-11-21
forum: Hardware &amp; Laptops
---

### Post by Startacus on 2007-11-21
I have a Nvidia 6600 and a VG1930wm 19" widescreen monitor. 

I'm in an interesting dilema. If I run "dpkg-reconfigure xserver-xorg" and select the old "nv" drivers then I can get the native resolution of the monitor at 1440x900 but then there is a big black bar on the left side of the monitor. 

If I go through "dpkg-reconfigure xserver-xorg" and choose the restricted "nvidia"  drivers then there is no black bar on the side but I can't access the 1440x900 resolution. 

I have done everything in "dpkg-reconfigure xserver-xorg" correctly, as far as I know, but this is not working.

Any suggestions would be greatly appreciated.

---

### Post by rmemm on 2007-11-21
I would look at /var/log/Xorg.0.log file and read down through it and find out why.  It should list the resolutions the monitor has and why they were rejected.

Once you find out why you can edit /etc/X11/xorg.conf file to fix the issue.  One caution about the conf file -- it's good to back it up before you modify it, and also to be ready with a recovery disk or to switch to console mode and use the command line interface if the X server does not load properly.

The format of the conf file is documented in man, and extra options that are driver specific are on a separate page named after the driver.

I'm betting that the resoluton you want is either not listed in xorg.conf, or the various refresh and scan frequency ranges in the monitor section are wrong for your monitor -- but I could be wrong.

Rob

---

### Post by EXCiD3 on 2007-11-21
Definitely use the nvidia driver. the nv driver doesnt support a lot of things.

If you have hte nvidia driver installed try using "sudo nvidia-xconfig" in console to have the nvidia driver configure your monitor for you.

manual configuration using the nvidia driver settings can be done by "sudo nvidia-settings" in console.

---

### Post by Startacus on 2007-11-22
Well, EXCiD3, I did that and I restarded the X server by doing a CTRL + ALT + backspace but when I try to access the settings it says "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xonfig' as root), and restart the X server. "

If I go to the Restricted Drivers Manager it says that the Nvidia acclerated graphics driver (latest cards) is in use. 

And, rmemm, I have no idea what I'm doing with that. I looked in the xconf and my resolution is listed there with a bunch of others but there are only two available for me to choose from when I boot.

When I boot into Ubuntu it says that it can't determine the graphics card and monitor. When I go to make any choices it boots into Ubuntu but the changes never take effect.

---

### Post by rmemm on 2007-11-22
Sorry if I'm not clear.  Here is a 2nd try.

My comment was based on my personal experience with my setup.  In my case there were missing resolutions for me as well, and missing refresh frequencies.  I for example like 1152x864 at 75 or 85 Hz -- which I know my monitor and video card supported.  I'm acutally using the nv driver -- mainly because my video card turns out to be one revision to old for the nvidia binary driver -- but same probably holdes for the binary driver.

The things that fixed my problem were the following changes to xorg.conf:

[LIST]
[*]Adding the HorizSync and the VertRefresh attribute to my "Monitor" Section.  
[*]Adding 1152x864 to the Modes line in the "Display" subsection of the "Screen" section.
[/LIST]

I too tried to add the resolution I wanted (that is 1152x864) but just adding it as one of the Modes didn't work for me.  The issue was that HorizSync, and VertRefresh didn't have the correct settings.

The reason these are important is that each pixel element of your display has to be written to the screen during every screen refresh.  The reason these are important is that if you specify a given monitor vertical refresh rate of say 85 Hz, then the screen has to be rewritten 85 times a second.  An 85 Hz refresh rate is only allowed to be used if the VertRefresh range specified either by default or in xorg.conf file includues 85Hz.

Horizontal sync speed is important also.  At a given screen resolution -- say 1152x864 means I have to write 864 lines  --  every 1/85th of a second (85 Hz vertical refresh).  If you use a higher resolution like say 1280x1024 then it's got to do 1024 lines every 1/85th of a second.   If the HorizSync frequency range either the default or the one listed in xorg.conf does not include the frequency you need to refresh the number of lines you specified in the resolution you want at the given vertical refresh rate -- then that resolution will be rejected as well.

The above was the problem I had.  For some reason Ubuntu defaults did not include 85Hz which I wanted, and didn't included the correct HorizSync setting to allow me to use 1152x864 resolution at 85 hr (or for that matter even 60 hz in my case).  The result was -- when I added 1152x864 to the Modes line it was just ignored.

I figured this out by looking at the log file I mentioned in the previous post as the log file --at least my log file -- listed in great detail all of the resolutions that the monitor should have had -- then later on in the log file it one by run rejected most of them based on the incompatibility with the default range frequency settings.  

Since I knew very well that my monitor had a wider bandwidth both in terms of VertRefresh and HorizSync -- I manually specified these based on what I found in my monitor manual -- and problem solved!

I of course don't know for sure this is your problem -- but what you described is very much like what I experienced -- an perhaps there is a pretty good change they are related.

Reguarding documentation.  I found the following man pages useful -- "man xorg.conf", and "man nv".  They describe the xorg.conf settings -- the general ones and the ones specific to the "nv" driver.  There may also be a man page or other doc for the binary driver -- but I don't have this installed -- so I don't know.

So I hope this helps.

Rob

---

