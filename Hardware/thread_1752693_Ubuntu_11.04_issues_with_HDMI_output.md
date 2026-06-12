---
title: "Ubuntu 11.04 issues with HDMI output"
date: 2011-05-08
forum: Hardware
---

### Post by BlacqWolf on 2011-05-08
I have a problem with the HDMI output, which I have going to a television, and I don't have a DVD/Blu Ray player in my room so I use my PC for playing movies, and of course I do that with the HDMI port. My problem is that the HDMI output isn't showing all the compatible resolutions in the Monitors application. It shows resolutions 640x480, 720x480, 1024x768, and 1440x900 (which is acceptable, except one problem: The TV doesn't support it). 

I would prefer to get it running at 1920x1080, as I can do in Windows, but I can't. I can get that option with the FGLRX driver installed, however it would then be impossible to watch video because then there would be HUGE performance drawbacks, and I can try disabling vsync completely in the Catalyst Control Center, however it the performance is still barely acceptable, and there are gigantic amounts of screen tearing on even lower frame rates. And here's the best part: When the FGLRX driver is installed, no matter what display settings I choose for the HDMI, it gives me a graphics notification saying a bunch of mumbo jumbo apparently meaning that the specified resolution is higher than 1600x1600, even if it's not. And I know my video card is compatible with it because I used to always be able to run HD video to my television at 1920x1080 with absolutely no graphics defects in Windows.

By the way, I'm using an AMD M880G w/ ATI Mobility Radeon HD 4200. Any help would be appreciated.

---

### Post by gtristian on 2011-05-09
Have you tried to start the computer with the tv connected ?

---

### Post by manicol on 2011-05-09
With Nvidia Drivers there is a way of showing a preview of the xorg.conf file that will be writen in /etc/X11/xorg.conf.
If this is possible also in your case you can set the monitor resolution to 1440x900 then copy the preview and open the xorg.conf file from a terminal:

```
sudo gedit /etc/X11/xorg.conf
```Then paste the text replacing the original one and manualy change the resolution from 1440x900 to 1920x1080 and save the file.

Now log-out and the new settings will take place.
I know this is not the best way of doing things but it works with me!

---

